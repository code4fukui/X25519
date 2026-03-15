# X25519.js

JavaScript ES moduleによるCurve25519の楕円曲線Diffie-Hellman鍵交換の実装です。

## 概要

暗号化の分野では、Curve25519は128ビットのセキュリティを提供する楕円曲線で、楕円曲線Diffie–Hellman (ECDH)鍵合意方式で使用されます。高速で特許のない、弱い乱数生成器にも強いのが特徴です。リファレンス実装はパブリックドメインのソフトウェアです。

Curve25519の論文では、それをDiffie–Hellman (DH)関数として定義しています。その後Daniel J. Bernsteinは、基礎となる曲線の名称をCurve25519、DH関数の名称をX25519とすることを提案しています。

## 使い方

```js
import { X25519 } from "https://code4fukui.github.io/X25519/X25519.js";
import { Ed25519 } from "https://code4fukui.github.io/Ed25519/Ed25519.js";
import { subbin } from "https://js.sabae.cc/binutil.js";

const user1 = Ed25519.generateKeyPair();
const pub1 = X25519.getPublic(subbin(user1.privateKey, 0, 32));
// pub1を user2に送る

const user2 = Ed25519.generateKeyPair();
const pub2 = X25519.getPublic(subbin(user2.privateKey, 0, 32));
// pub2を user1に送る

// user1
const shared1 = X25519.getSharedKey(subbin(user1.privateKey, 0, 32), pub2);
// user2 
const shared2 = X25519.getSharedKey(subbin(user2.privateKey, 0, 32), pub1);
console.log(shared1, shared2);
```

## 作者

* [Mykola Bubelich](https://bubelich.com)

## プロジェクト

* [CryptoEsel](https://cryptoesel.com) - 安全かつ確実なファイル転送

## リンク

* http://tweetnacl.cr.yp.to/
* https://github.com/dchest/tweetnacl-js
* https://github.com/rev22/curve255js/
* http://www.flownet.com/ron/code/djbec.js
* https://cr.yp.to/ecdh.html
* https://gnunet.org/svn/gnunet-java/src/main/java/org/gnunet/util/crypto/Ed25519.java
* http://www.movable-type.co.uk/scripts/sha256.html
* http://samuelkerr.com/?p=431