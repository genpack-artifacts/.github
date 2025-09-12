## genpack-artifacts

このogranizationは genpackアーティファクトのリポジトリを集めたものです。genpackとは、genpack.json5 というファイルの内容に基づいてGentoo Linuxの stage3をベースに自動的にOSイメージ（物理マシン、仮想マシンで実行可能）をビルドするツールです。生成物(squashfsファイル)をアーティファクトと読んでいます。

### genpack.json5について

- packages: OSイメージに含めるebuildパッケージのリスト
  - genpack/paravirt: 仮想マシン前提の構成を示すメタパッケージ
  - genpack/systemimg: 物理マシンまたはフルバーチャルの仮想マシンを前提とした構成を示すメタパッケージ

### genpackのディレクトリ構造

- files/: OSイメージに含むための任意のファイル・ディレクトリ
  - files/build.d: アーティファクト生成時に実行する任意のスクリプトがこのディレクトリ以下に収められています。たとえば、ebuildがないため独自のセットアップ処理を要するソフトウェアのためのスクリプトや、ebuildでインストールされたソフトウェアの設定をカスタマイズするスクリプトなどがここに配置されます。このディレクトリは生成されるOSイメージからは除外されます。
- patches/: ビルド時にソースに適用するパッチです。/etc/portage/patches としてビルド環境にコピーされます
- overlay/: ビルド環境に適用するPortageオーバーレイがあればこのディレクトリに配置します。
