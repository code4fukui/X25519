# X25519.js

JavaScript ES module implementation of Elliptic curve Diffie-Hellman key exchange over Curve25519

## Description

In cryptography, Curve25519 is an elliptic curve offering 128 bits of security and designed for use with the elliptic curve Diffie–Hellman (ECDH) key agreement scheme. It is one of the fastest ECC curves; it is not covered by any known patents, and it is less susceptible to weak random-number generators. The reference implementation is public domain software.

The original Curve25519 paper defined it as a Diffie–Hellman (DH) function. Daniel J. Bernstein has since proposed that the name Curve25519 be used for the underlying curve, and the name X25519 for the DH function.

## Usage

```js
import { X25519 } from "https://code4fukui.github.io/X25519/X25519.js";
import { Ed25519 } from "https://code4fukui.github.io/Ed25519/Ed25519.js";
import { subbin } from "https://js.sabae.cc/binutil.js";

const user1 = Ed25519.generateKeyPair();
const pub1 = X25519.getPublic(subbin(user1.privateKey, 0, 32));
// send pub1 to user2

const user2 = Ed25519.generateKeyPair();
const pub2 = X25519.getPublic(subbin(user2.privateKey, 0, 32));
// send pub2 to user1

// user1
const shared1 = X25519.getSharedKey(subbin(user1.privateKey, 0, 32), pub2);
// user2
const shared2 = X25519.getSharedKey(subbin(user2.privateKey, 0, 32), pub1);
console.log(shared1, shared2);
```

## Authors

* [Mykola Bubelich](https://bubelich.com) 

## Projects

* [CryptoEsel](https://cryptoesel.com) - Safe and secure file transfer

## Links

* http://tweetnacl.cr.yp.to/
* https://github.com/dchest/tweetnacl-js
* https://github.com/rev22/curve255js/
* http://www.flownet.com/ron/code/djbec.js
* https://cr.yp.to/ecdh.html
* https://gnunet.org/svn/gnunet-java/src/main/java/org/gnunet/util/crypto/Ed25519.java
* http://www.movable-type.co.uk/scripts/sha256.html
* http://samuelkerr.com/?p=431

