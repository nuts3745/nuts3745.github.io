---
layout: "page"
title: "BitcoinLayer2周りについて"
---
久しぶりにBitcoin関連の[イベント](https://hashhub.connpass.com/event/164831/)に参加してきた。
これまでほとんどEthereum関連のリサーチしかしてなかったから新しい情報が多くて面白かった。
自分が疎すぎて名前も聞いたことなかったけど、BlockstreamとCryptoGarageの人たちが発表していた。
DigitalGarage関連のジョイントベンチャーでBitcoinに注力している会社がCryptoGarageらしい。
主に技術面でのサポートかもしれないけど、BlockstreamもCryptoGarageに出資しているらしい。
日本にもこれだけ技術開発に力入れているところがあるのは知らなかった。

### Liquid Network

[LiquidNetworkDocument](https://docs.blockstream.com/liquid/technical_overview.html)

ひとつめの発表はLiquidNetworkについてだった。
- Blockstreamが開発しているBitcoinのSideChain。
![sidechain](https://docs.blockstream.com/_images/sidechain.png)
- Elementsで実装されている。
- BTCにペグしたLiquidBTCと相互交換できる。
- ERCトークンみたいにAssetも発行できる。

英語で詳しくはよくわからんかったのは秘密。

### Lightning Network WatchTower

- Lightning Networkの問題点
  - Payment Channelを閉じるには、双方のWalletがオンラインなのが前提となっている。
    - Payment Channelを開いた状態でWalletが長時間オフラインになってしまうと、悪意のある人が送金前にステートを書き換えられるリスクができてしまう。
  - Nodeが落ちた場合は、ユーザーがCheatしたとみなされてPunishされる可能性がある。
- WatchTowerで監視する。
  - ステートが変更される度にWatchTowerに暗号化された文字列が送信される。
  - Payment Channelが閉じられたときに、適切なステートかどうかTransactionIDと文字列とで検証して、復号できなかった場合（=ステートを書き換えた悪意のあるユーザーがいた）、DepositされたBTCは全て誠意のあるユーザーへと送金される。

### Discreet Log Contracts

- Bitcoinで発行できるSmartContract
- 現実の信頼性を表現するoracleを利用しているのが特徴。
- 仕組みはLightning Networkに似ている。
- セキュリティがとても強固であるBitcoinで金融商品を提供できるのが強み。
- [OSS](https://github.com/discreetlogcontracts/dlcspecs/)も始めた。