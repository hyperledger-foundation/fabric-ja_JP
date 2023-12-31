# peer channel

`peer channel` コマンドを使用すると、管理者はピアに対してチャネルに関連した操作を実行できます。
例えば、チャネルに参加したり、ピアが参加しているチャネルを一覧で表示したりできます。

## Syntax

`peer channel` コマンドは、以下のサブコマンドを持っています。:

  * create
  * fetch
  * getinfo
  * join
  * list
  * signconfigtx
  * update

## peer channel
```
Operate a channel: create|fetch|join|list|update|signconfigtx|getinfo.

Usage:
  peer channel [command]

Available Commands:
  create       Create a channel
  fetch        Fetch a block
  getinfo      get blockchain information of a specified channel.
  join         Joins the peer to a channel.
  list         List of channels peer has joined.
  signconfigtx Signs a configtx update.
  update       Send a configtx update.

Flags:
      --cafile string                       Path to file containing PEM-encoded trusted certificate(s) for the ordering endpoint
      --certfile string                     Path to file containing PEM-encoded X509 public key to use for mutual TLS communication with the orderer endpoint
      --clientauth                          Use mutual TLS when communicating with the orderer endpoint
      --connTimeout duration                Timeout for client to connect (default 3s)
  -h, --help                                help for channel
      --keyfile string                      Path to file containing PEM-encoded private key to use for mutual TLS communication with the orderer endpoint
  -o, --orderer string                      Ordering service endpoint
      --ordererTLSHostnameOverride string   The hostname override to use when validating the TLS connection to the orderer
      --tls                                 Use TLS when communicating with the orderer endpoint
      --tlsHandshakeTimeShift duration      The amount of time to shift backwards for certificate expiration checks during TLS handshakes with the orderer endpoint

Use "peer channel [command] --help" for more information about a command.
```


## peer channel create
```
Create a channel and write the genesis block to a file.

Usage:
  peer channel create [flags]

Flags:
  -c, --channelID string     In case of a newChain command, the channel ID to create. It must be all lower case, less than 250 characters long and match the regular expression: [a-z][a-z0-9.-]*
  -f, --file string          Configuration transaction file generated by a tool such as configtxgen for submitting to orderer
  -h, --help                 help for create
      --outputBlock string   The path to write the genesis block for the channel. (default ./<channelID>.block)
  -t, --timeout duration     Channel creation timeout (default 10s)

Global Flags:
      --cafile string                       Path to file containing PEM-encoded trusted certificate(s) for the ordering endpoint
      --certfile string                     Path to file containing PEM-encoded X509 public key to use for mutual TLS communication with the orderer endpoint
      --clientauth                          Use mutual TLS when communicating with the orderer endpoint
      --connTimeout duration                Timeout for client to connect (default 3s)
      --keyfile string                      Path to file containing PEM-encoded private key to use for mutual TLS communication with the orderer endpoint
  -o, --orderer string                      Ordering service endpoint
      --ordererTLSHostnameOverride string   The hostname override to use when validating the TLS connection to the orderer
      --tls                                 Use TLS when communicating with the orderer endpoint
      --tlsHandshakeTimeShift duration      The amount of time to shift backwards for certificate expiration checks during TLS handshakes with the orderer endpoint
```


## peer channel fetch
```
Fetch a specified block, writing it to a file.

Usage:
  peer channel fetch <newest|oldest|config|(number)> [outputfile] [flags]

Flags:
      --bestEffort         Whether fetch requests should ignore errors and return blocks on a best effort basis
  -c, --channelID string   In case of a newChain command, the channel ID to create. It must be all lower case, less than 250 characters long and match the regular expression: [a-z][a-z0-9.-]*
  -h, --help               help for fetch

Global Flags:
      --cafile string                       Path to file containing PEM-encoded trusted certificate(s) for the ordering endpoint
      --certfile string                     Path to file containing PEM-encoded X509 public key to use for mutual TLS communication with the orderer endpoint
      --clientauth                          Use mutual TLS when communicating with the orderer endpoint
      --connTimeout duration                Timeout for client to connect (default 3s)
      --keyfile string                      Path to file containing PEM-encoded private key to use for mutual TLS communication with the orderer endpoint
  -o, --orderer string                      Ordering service endpoint
      --ordererTLSHostnameOverride string   The hostname override to use when validating the TLS connection to the orderer
      --tls                                 Use TLS when communicating with the orderer endpoint
      --tlsHandshakeTimeShift duration      The amount of time to shift backwards for certificate expiration checks during TLS handshakes with the orderer endpoint
```


## peer channel getinfo
```
get blockchain information of a specified channel. Requires '-c'.

Usage:
  peer channel getinfo [flags]

Flags:
  -c, --channelID string   In case of a newChain command, the channel ID to create. It must be all lower case, less than 250 characters long and match the regular expression: [a-z][a-z0-9.-]*
  -h, --help               help for getinfo

Global Flags:
      --cafile string                       Path to file containing PEM-encoded trusted certificate(s) for the ordering endpoint
      --certfile string                     Path to file containing PEM-encoded X509 public key to use for mutual TLS communication with the orderer endpoint
      --clientauth                          Use mutual TLS when communicating with the orderer endpoint
      --connTimeout duration                Timeout for client to connect (default 3s)
      --keyfile string                      Path to file containing PEM-encoded private key to use for mutual TLS communication with the orderer endpoint
  -o, --orderer string                      Ordering service endpoint
      --ordererTLSHostnameOverride string   The hostname override to use when validating the TLS connection to the orderer
      --tls                                 Use TLS when communicating with the orderer endpoint
      --tlsHandshakeTimeShift duration      The amount of time to shift backwards for certificate expiration checks during TLS handshakes with the orderer endpoint
```


## peer channel join
```
Joins the peer to a channel.

Usage:
  peer channel join [flags]

Flags:
  -b, --blockpath string   Path to file containing genesis block
  -h, --help               help for join

Global Flags:
      --cafile string                       Path to file containing PEM-encoded trusted certificate(s) for the ordering endpoint
      --certfile string                     Path to file containing PEM-encoded X509 public key to use for mutual TLS communication with the orderer endpoint
      --clientauth                          Use mutual TLS when communicating with the orderer endpoint
      --connTimeout duration                Timeout for client to connect (default 3s)
      --keyfile string                      Path to file containing PEM-encoded private key to use for mutual TLS communication with the orderer endpoint
  -o, --orderer string                      Ordering service endpoint
      --ordererTLSHostnameOverride string   The hostname override to use when validating the TLS connection to the orderer
      --tls                                 Use TLS when communicating with the orderer endpoint
      --tlsHandshakeTimeShift duration      The amount of time to shift backwards for certificate expiration checks during TLS handshakes with the orderer endpoint
```


## peer channel list
```
List of channels peer has joined.

Usage:
  peer channel list [flags]

Flags:
  -h, --help   help for list

Global Flags:
      --cafile string                       Path to file containing PEM-encoded trusted certificate(s) for the ordering endpoint
      --certfile string                     Path to file containing PEM-encoded X509 public key to use for mutual TLS communication with the orderer endpoint
      --clientauth                          Use mutual TLS when communicating with the orderer endpoint
      --connTimeout duration                Timeout for client to connect (default 3s)
      --keyfile string                      Path to file containing PEM-encoded private key to use for mutual TLS communication with the orderer endpoint
  -o, --orderer string                      Ordering service endpoint
      --ordererTLSHostnameOverride string   The hostname override to use when validating the TLS connection to the orderer
      --tls                                 Use TLS when communicating with the orderer endpoint
      --tlsHandshakeTimeShift duration      The amount of time to shift backwards for certificate expiration checks during TLS handshakes with the orderer endpoint
```


## peer channel signconfigtx
```
Signs the supplied configtx update file in place on the filesystem. Requires '-f'.

Usage:
  peer channel signconfigtx [flags]

Flags:
  -f, --file string   Configuration transaction file generated by a tool such as configtxgen for submitting to orderer
  -h, --help          help for signconfigtx

Global Flags:
      --cafile string                       Path to file containing PEM-encoded trusted certificate(s) for the ordering endpoint
      --certfile string                     Path to file containing PEM-encoded X509 public key to use for mutual TLS communication with the orderer endpoint
      --clientauth                          Use mutual TLS when communicating with the orderer endpoint
      --connTimeout duration                Timeout for client to connect (default 3s)
      --keyfile string                      Path to file containing PEM-encoded private key to use for mutual TLS communication with the orderer endpoint
  -o, --orderer string                      Ordering service endpoint
      --ordererTLSHostnameOverride string   The hostname override to use when validating the TLS connection to the orderer
      --tls                                 Use TLS when communicating with the orderer endpoint
      --tlsHandshakeTimeShift duration      The amount of time to shift backwards for certificate expiration checks during TLS handshakes with the orderer endpoint
```


## peer channel update
```
Signs and sends the supplied configtx update file to the channel. Requires '-f', '-o', '-c'.

Usage:
  peer channel update [flags]

Flags:
  -c, --channelID string   In case of a newChain command, the channel ID to create. It must be all lower case, less than 250 characters long and match the regular expression: [a-z][a-z0-9.-]*
  -f, --file string        Configuration transaction file generated by a tool such as configtxgen for submitting to orderer
  -h, --help               help for update

Global Flags:
      --cafile string                       Path to file containing PEM-encoded trusted certificate(s) for the ordering endpoint
      --certfile string                     Path to file containing PEM-encoded X509 public key to use for mutual TLS communication with the orderer endpoint
      --clientauth                          Use mutual TLS when communicating with the orderer endpoint
      --connTimeout duration                Timeout for client to connect (default 3s)
      --keyfile string                      Path to file containing PEM-encoded private key to use for mutual TLS communication with the orderer endpoint
  -o, --orderer string                      Ordering service endpoint
      --ordererTLSHostnameOverride string   The hostname override to use when validating the TLS connection to the orderer
      --tls                                 Use TLS when communicating with the orderer endpoint
      --tlsHandshakeTimeShift duration      The amount of time to shift backwards for certificate expiration checks during TLS handshakes with the orderer endpoint
```

## Example Usage

### peer channel create examples

`peer channel create` コマンドで `--orderer` globalフラグを使用する例を以下に示します。

* ファイル `./createchannel.tx` のコンフィギュレーショントランザクションで定義されたチャネル `mychannel` を作成します。
  `orderer.example.com:7050` のOrdererを使用します。

  ```
  peer channel create -c mychannel -f ./createchannel.tx --orderer orderer.example.com:7050

  2018-02-25 08:23:57.548 UTC [channelCmd] InitCmdFactory -> INFO 003 Endorser and orderer connections initialized
  2018-02-25 08:23:57.626 UTC [channelCmd] InitCmdFactory -> INFO 019 Endorser and orderer connections initialized
  2018-02-25 08:23:57.834 UTC [channelCmd] readBlock -> INFO 020 Received block: 0
  2018-02-25 08:23:57.835 UTC [main] main -> INFO 021 Exiting.....

  ```

  チャネルが正常に作成されたことを示すブロック0が返されます。

`peer channel create` コマンドオプションの使用例を以下に示します。

* IPアドレス `orderer.example.com:7050` のOrdererを使用して、ネットワークに新しいチャネル `mychannel` を作成します。
  このチャネルを作成するために必要なコンフィギュレーション更新トランザクションは、ファイル `./createchannel.tx` で定義されています。
  チャネルが作成されるまで 30 秒待ちます。

  ```
    peer channel create -c mychannel --orderer orderer.example.com:7050 -f ./createchannel.tx -t 30s

    2018-02-23 06:31:58.568 UTC [channelCmd] InitCmdFactory -> INFO 003 Endorser and orderer connections initialized
    2018-02-23 06:31:58.669 UTC [channelCmd] InitCmdFactory -> INFO 019 Endorser and orderer connections initialized
    2018-02-23 06:31:58.877 UTC [channelCmd] readBlock -> INFO 020 Received block: 0
    2018-02-23 06:31:58.878 UTC [main] main -> INFO 021 Exiting.....

    ls -l

    -rw-r--r-- 1 root root 11982 Feb 25 12:24 mychannel.block

  ```

  チャネル `mychannel` が正常に作成されていることが分かります。
  出力に示されているように、ブロック0(ゼロ)がこのチャネルのブロックチェーンに追加され、ピアに返されます。
  そのブロックは、ローカルディレクトリに `mychannel.block` として保存されます。

  ブロック0は、チャネルの初期設定を提供するので、しばしば *ジェネシスブロック* と呼ばれます。
  チャネルに対する後続のすべての更新は、そのチャネルのブロックチェーンに対する
  コンフィギュレーションブロックとしてキャプチャされ、以前の設定に取って代わります。

### peer channel fetch example

`peer channel fetch` コマンドの例を以下に示します。

* `newest` オプションを使用して、最新のチャネルブロックを取得し、
  ファイル `mychannel.block` に保存します。

  ```
  peer channel fetch newest mychannel.block -c mychannel --orderer orderer.example.com:7050

  2018-02-25 13:10:16.137 UTC [channelCmd] InitCmdFactory -> INFO 003 Endorser and orderer connections initialized
  2018-02-25 13:10:16.144 UTC [channelCmd] readBlock -> INFO 00a Received block: 32
  2018-02-25 13:10:16.145 UTC [main] main -> INFO 00b Exiting.....

  ls -l

  -rw-r--r-- 1 root root 11982 Feb 25 13:10 mychannel.block

  ```

  取得したブロックは32番であること、また、
  その情報はファイル `mychannel.block` に書き込まれたことが分かります。

* `(block number)` オプションを使用して、特定のブロック
  -- このケースでは、ブロック番号16 -- を取得し、デフォルトのブロックファイルに保存します。

  ```
  peer channel fetch 16  -c mychannel --orderer orderer.example.com:7050

  2018-02-25 13:46:50.296 UTC [channelCmd] InitCmdFactory -> INFO 003 Endorser and orderer connections initialized
  2018-02-25 13:46:50.302 UTC [channelCmd] readBlock -> INFO 00a Received block: 16
  2018-02-25 13:46:50.302 UTC [main] main -> INFO 00b Exiting.....

  ls -l

  -rw-r--r-- 1 root root 11982 Feb 25 13:10 mychannel.block
  -rw-r--r-- 1 root root  4783 Feb 25 13:46 mychannel_16.block

  ```

  取得したブロックは16番であること、また、
  その情報はデフォルトのファイル `mychannel_16.block` に書き込まれたことが分かります。

  コンフィギュレーションブロックの場合、ブロックファイルは [`configtxlator` コマンド](./configtxlator.html) を使用してデコードできます。
  デコードされた出力の例については、このコマンドを参照してください。
  ユーザーのトランザクションブロックもデコードできますが、
  これを行うにはユーザーがプログラムを書く必要があります。

### peer channel getinfo example

`peer channel getinfo` コマンドの例を以下に示します。

* チャネル `mychannel` のローカルピアに関する情報を取得します。

  ```
  peer channel getinfo -c mychannel

  2018-02-25 15:15:44.135 UTC [channelCmd] InitCmdFactory -> INFO 003 Endorser and orderer connections initialized
  Blockchain info: {"height":5,"currentBlockHash":"JgK9lcaPUNmFb5Mp1qe1SVMsx3o/22Ct4+n5tejcXCw=","previousBlockHash":"f8lZXoAn3gF86zrFq7L1DzW2aKuabH9Ow6SIE5Y04a4="}
  2018-02-25 15:15:44.139 UTC [main] main -> INFO 006 Exiting.....

  ```

  チャネル `mychannel` の最新ブロックがブロック5であることが分かります。
  そのチャネルのブロックチェーンにおける最新ブロックの暗号ハッシュも確認できます。

### peer channel join example

`peer channel join` コマンドの例を以下に示します。

* ファイル `./mychannel.genesis.block` で識別されるジェネシスブロックで定義されたチャネルにピアを参加させます。
  この例では、チャネルブロックは `peer channel fetch` コマンドで取得済です。

  ```
  peer channel join -b ./mychannel.genesis.block

  2018-02-25 12:25:26.511 UTC [channelCmd] InitCmdFactory -> INFO 003 Endorser and orderer connections initialized
  2018-02-25 12:25:26.571 UTC [channelCmd] executeJoin -> INFO 006 Successfully submitted proposal to join channel
  2018-02-25 12:25:26.571 UTC [main] main -> INFO 007 Exiting.....

  ```

  ピアがチャネルへの参加要求を正常に行ったことがわかります。

### peer channel list example

`peer channel list` コマンドの例を以下に示します。

  * ピアが参加しているチャネルを一覧表示します。

    ```
    peer channel list

    2018-02-25 14:21:20.361 UTC [channelCmd] InitCmdFactory -> INFO 003 Endorser and orderer connections initialized
    Channels peers has joined:
    mychannel
    2018-02-25 14:21:20.372 UTC [main] main -> INFO 006 Exiting.....

    ```

    ピアがチャネル `mychannel` に参加していることが分かります。

### peer channel signconfigtx example

`peer channel signconfigtx` コマンドの例を以下に示します。

* ファイル `./updatechannel.tx` で定義されている `channel update` トランザクションに署名します。
  この例では、コマンド実行前後のコンフィギュレーショントランザクションファイルを一覧表示しています。

  ```
  ls -l

  -rw-r--r--  1 anthonyodowd  staff   284 25 Feb 18:16 updatechannel.tx

  peer channel signconfigtx -f updatechannel.tx

  2018-02-25 18:16:44.456 GMT [channelCmd] InitCmdFactory -> INFO 001 Endorser and orderer connections initialized
  2018-02-25 18:16:44.459 GMT [main] main -> INFO 002 Exiting.....

  ls -l

  -rw-r--r--  1 anthonyodowd  staff  2180 25 Feb 18:16 updatechannel.tx

  ```

  ファイル `updatechannel.tx` のサイズが284バイトから2180バイトに増加していることから、
  ピアがコンフィギュレーショントランザクションに正常に署名したことが分かります。

### peer channel update example

`peer channel update` コマンドの例を以下に示します。

* ファイル `./updatechannel.tx` で定義されたコンフィギュレーショントランザクションを使用して、
  チャネル `mychannel` を更新します。
  IPアドレス `orderer.example.com:7050` のOrdererを使用して、
  チャネル内のすべてのピアにコンフィギュレーショントランザクションを送信し、チャネルコンフィギュレーションのコピーを更新します。

  ```
  peer channel update -c mychannel -f ./updatechannel.tx -o orderer.example.com:7050

  2018-02-23 06:32:11.569 UTC [channelCmd] InitCmdFactory -> INFO 003 Endorser and orderer connections initialized
  2018-02-23 06:32:11.626 UTC [main] main -> INFO 010 Exiting.....

  ```

  この時点で、チャネル `mychannel` が正常に更新されました。

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.
