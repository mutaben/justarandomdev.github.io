---
layout: post
title:  "From Pseudo-Random Number Generators to TOTP with Swift - Part 1"
date:   2019-12-28 00:00:01 +0100
---

Randomness is pretty fascinating. One could argue that what we perceive as random is just a combination of hardly predictable causality.

As for our machines, they are built and engineered conceptually and physically to be the very definition of deterministic. When we develop, we want our programs to be as predictable as possible, and we try to eliminate any source of unknown behaviour. We like our bugs to be replicable.

Yet randomness is essential in Software Engineering, and somehow, we have to manage to create a little bit of chaos out of all this order.

Let's start with a simple problem. Have you ever wondered how does a [car remote control][keyless-system] works? Aside from the radio waves stuff, its security aspect is a little bit off putting. Indeed, it must meets a few needs:

- A car remote should open one and only one car (and reciprocally the car should also accept this car remote)
- The duplicate of this remote should also be able to open the car
- If lost, we should be able to manufacture a new remote control from the VIN

Simple right? Just put a secret combination in both the car and the remote and you're done?

Not quite, because one could eavesdrop the radio signal sent from the remote, and build another key fob for your car.

So the code has to be changing, in order to avoid replay attacks.

It has to be changing, _and_ it must be changing in the same way on the car and the remote.

Well, conveniently, that's one property of pseudo-random number generators. If seeded with the same number, they will generate (pseudo) random numbers, exactly in sync. For instance, seed both micro controllers of the car and the remote with the number 1729 (a number with a [beautiful story][cabby-number]), and you will have the same sequence generated on both sides, for instance 917, 924, 87, 494, 465 (with a boundary of 1000).

On the implementation side with [Swift's standard library][randomnumbergenerator], it would look like this:

{% highlight swift %}
struct CarKeyRNG: RandomNumberGenerator {
    var seed: UInt64

    init(seed: UInt64) {
        self.seed = seed
    }

    mutating func next() -> UInt64 {
        seed = 6364136223846793005 &* seed &+ 1442695040888963407
        return seed
    }
}

var carRng = CarKeyRNG(seed: 1729)

// Generate random numbers by overriding the default RNG with ours
Int.random(in: 1...1000, using: &carRng) // 917
Int.random(in: 1...1000, using: &carRng) // 924
Int.random(in: 1...1000, using: &carRng) // 87
Int.random(in: 1...1000, using: &carRng) // 494
Int.random(in: 1...1000, using: &carRng) // 465
{% endhighlight %}

We used a simple implementation of [Linear Congruential Random Number Generator][lcrng], with commonly used multiplier and increment. Then we seeded it with 1729, and plucked out the first five numbers by overriding the default [`SystemRandomNumberGenerator`][srng].

The ampersand before the multiplication and the addition ensures we wrap around the `UInt64` type in case we overflow.

**This is just an implementation example, please do not use it in production unless you've properly reviewed its cryptographic accuracy!**

So with this hypothetical code in your car and its remotes, you just have to seed them with the same secret initial value. You can program a new key fob fresh from the factory to work with your car. Everything is fine right?

Well there's a last piece missing. Let's say somebody activates the remote key out of range. The key fob will have used a few numbers, and the car will not have received them, they will be out of sync.

What happens next time you try to open your car?

Well first, the controller on the car will keep a sliding window of acceptable codes, for instance the last and next ten around a given seed.

But what if you went all out and really smashed the buttons a hundred, a thousand times? Or what about the spare key fob, which isn't in sync at all?

The bad news is that you will probably have to manually open your car, with the actual key. The good news is, your remote key fob is not out of order. When you will insert the key in the car's keyway to start it, it will electronically sync with the on board system to be on the same page, i.e. have the current seed be the same. Then they will start generating the same numbers again.

Something along those lines would happen:

{% highlight swift %}
var carRng = CarKeyRNG(seed: 1729)
var carKeyRng = CarKeyRNG(seed: 1729)

// Generate numbers only on the key side
Int.random(in: 1...1000, using: &carKeyRng) // 917
Int.random(in: 1...1000, using: &carKeyRng) // 924
Int.random(in: 1...1000, using: &carKeyRng) // 87
Int.random(in: 1...1000, using: &carKeyRng) // 494
Int.random(in: 1...1000, using: &carKeyRng) // 465

// They're out of sync, let's make them sync
carRng.seed = carKeyRng.seed

Int.random(in: 1...1000, using: &carKeyRng) // 312
Int.random(in: 1...1000, using: &carRng) // 312
// They're in sync again

{% endhighlight %}

Smart isn't it?

Let's recap:

- Your car and its remotes are factory set to have a same (hopefully) unique seed so that they will generate a same unique sequence of numbers
- The car accepts a window of valid codes to allow for some small desynchronisation
- The seed will be synced each time the key enters the car

I think that's a fun problem, solved in an elegant way. But we are not (yet?) programming our cars systems with Swift.

That brings us to our next topic. Have you ever wondered how two-factor authentication works? Not the SMS kind (although it follows pretty much the same principles), the TOTP one. When you have a [physical device][yubikey], or an app like 1Password or Authy generating a one time password to supplement after entering your password, as an additional security layer.

Unlike the common (and unfortunately unsecure) SMS method, which is a two-step authentication, this method is a two factor one. It relies on a different factor than the password. The password is something _you know_ whereas the one-time password from a device or app is _something you have_. (The third common factor is usually biometric, meaning _something you are_.)

The basics are the same, but the implementation differs since we don't rely on only an initial seed, but current time is used as well.

If it piqued your interest, stay tuned for part two, where we will explore TOTP with Swift! 

[keyless-system]: https://en.wikipedia.org/wiki/Remote_keyless_system
[cabby-number]: https://en.wikipedia.org/wiki/1729_%28number%29
[randomnumbergenerator]: https://developer.apple.com/documentation/swift/randomnumbergenerator
[lcrng]: https://en.wikipedia.org/wiki/Linear_congruential_generator
[srng]: https://developer.apple.com/documentation/swift/systemrandomnumbergenerator
[yubikey]: https://en.wikipedia.org/wiki/YubiKey

