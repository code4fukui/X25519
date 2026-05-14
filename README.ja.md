# X25519.js

Curve25519上の楕円曲線ディフィー・ヘルマン鍵交換のJavaScript ESモジュール実装。

## 概要

暗号技術において、Curve25519は128ビットのセキュリティを提供し、楕円曲線ディフィー・ヘルマン（ECDH）鍵合意スキームでの使用を目的として設計された楕円曲線です。最も高速なECC（楕円曲線暗号）曲線の一つであり、既知の特許の対象ではなく、弱い乱数生成器の影響を受けにくいという特徴があります。参照実装はパブリックドメインソフトウェアです。

オリジナルのCurve25519の論文では、これをディフィー・ヘルマン（DH）関数として定義していました。その後、Daniel J. Bernsteinは、基となる曲線にCurve25519という名称を使用し、DH関数にX25519という名称を使用することを提案しました。

## 使い方

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

## 著者

* [Mykola Bubelich](https://bubelich.com)

## プロジェクト

* [CryptoEsel](https://cryptoesel.com) - 安全でセキュアなファイル転送

## リンク

* http://tweetnacl.cr.yp.to/
* https://github.com/dchest/tweetnacl-js
* https://github.com/rev22/curve255js/
* http://www.flownet.com/ron/code/djbec.js
* https://cr.yp.to/ecdh.html
* https://gnunet.org/svn/gnunet-java/src/main/java/org/gnunet/util/crypto/Ed25519.java
* http://www.movable-type.co.uk/scripts/sha256.html
* http://samuelkerr.com/?p=431

## ライセンス

MIT License — 詳細は [LICENSE](LICENSE) を参照してください。
