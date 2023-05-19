# Quantum Mechanical Keyboard Firmware

[![Current Version](https://img.shields.io/github/tag/qmk/qmk_firmware.svg)](https://github.com/qmk/qmk_firmware/tags)
[![Discord](https://img.shields.io/discord/440868230475677696.svg)](https://discord.gg/Uq7gcHh)
[![Docs Status](https://img.shields.io/badge/docs-ready-orange.svg)](https://docs.qmk.fm)
[![GitHub contributors](https://img.shields.io/github/contributors/qmk/qmk_firmware.svg)](https://github.com/qmk/qmk_firmware/pulse/monthly)
[![GitHub forks](https://img.shields.io/github/forks/qmk/qmk_firmware.svg?style=social&label=Fork)](https://github.com/qmk/qmk_firmware/)

This is a keyboard firmware based on the [tmk\_keyboard firmware](https://github.com/tmk/tmk_keyboard) with some useful features for Atmel AVR and ARM controllers, and more specifically, the [OLKB product line](https://olkb.com), the [ErgoDox EZ](https://ergodox-ez.com) keyboard, and the [Clueboard product line](https://clueboard.co).

## Documentation

* [See the official documentation on docs.qmk.fm](https://docs.qmk.fm)

The docs are powered by [Docsify](https://docsify.js.org/) and hosted on [GitHub](/docs/). They are also viewable offline; see [Previewing the Documentation](https://docs.qmk.fm/#/contributing?id=previewing-the-documentation) for more details.

You can request changes by making a fork and opening a [pull request](https://github.com/qmk/qmk_firmware/pulls), or by clicking the "Edit this page" link at the bottom of any page.

## Supported Keyboards

* [Planck](/keyboards/planck/)
* [Preonic](/keyboards/preonic/)
* [ErgoDox EZ](/keyboards/ergodox_ez/)
* [Clueboard](/keyboards/clueboard/)
* [Cluepad](/keyboards/clueboard/17/)
* [Atreus](/keyboards/atreus/)

The project also includes community support for [lots of other keyboards](/keyboards/).

## Maintainers

QMK is developed and maintained by Jack Humbert of OLKB with contributions from the community, and of course, [Hasu](https://github.com/tmk). The OLKB product firmwares are maintained by [Jack Humbert](https://github.com/jackhumbert), the Ergodox EZ by [ZSA Technology Labs](https://github.com/zsa), the Clueboard by [Zach White](https://github.com/skullydazed), and the Atreus by [Phil Hagelberg](https://github.com/technomancy).

## Official Website

[qmk.fm](https://qmk.fm) is the official website of QMK, where you can find links to this page, the documentation, and the keyboards supported by QMK.

## Note about install to Moonlander Mk I
Ubuntu上で、下記の手順を踏むことでMoonlander Mk Iにファームウェアを書き込めることを確認した
1. [QMK Firmware](https://github.com/qmk/qmk_firmware)のリポジトリをcloneする
zipでのダウンロードだと、後続の手順がうまくいかなかった
2. `make git-submodule` する
3. [こちら](https://github.com/qmk/qmk_firmware/tree/master/keyboards/moonlander)の配下にMoonlander Mk I用のファイルがあるのを確認する
4. 前項のディレクトリにyusukeディレクトリがあることを確認する
5. リポジトリのルートディレクトリに `cd` し、下記を実行してファームウェアをビルドする  
  ビルドするキーマップは `:` の後に指定する模様
  ```sh
  util/docker_build.sh moonlander:yusuke
  ```
6. 前項の処理が終わると、リポジトリのルートディレクトリにビルドされたファームウェアのbinが格納されているはずなので確認する
7. 前項で確認したbinファイルを取得して、WallyでMoonlander Mk Iにファームウェアをインストールする

* VIAをインストールしてRemapを使うことも可能
  * Remapに読ませるjsonファイルも、Moonlander Mk I用が https://github.com/the-via/keyboards/blob/master/src/zsa/moonlander.json で提供されている  
  * しかしRemapでは、ファームウェア？VIA？のバージョンに依って、設定の書き込みができないなどの問題がある模様  
    少なくとも当方の環境では、キーマップの保存機能とキーボードへの書き込み機能を使うことができなかった
  * QMK Firmwareのkeymap.cを、キーマップの変更の為に直接変更するのは然程手間ではないので、こちらの方法を利用するのが吉  
    ファームウェアのビルドとキーボードへの書き込みに時間がかかるので注意すること  
    特に初回のファームウェアのビルドは30分くらい掛かった
