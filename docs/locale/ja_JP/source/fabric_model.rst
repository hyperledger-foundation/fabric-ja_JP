Hyperledger Fabric モデル
=====================================================

このセクションでは、Hyperledger Fabricに組み込まれた、包括的でありながら
カスタマイズ可能なエンタープライズブロックチェーンソリューションとしての役割を果たす
主要な設計機能の概要を説明します:

* `資産`_ --- 資産の定義によって、自然食品からクラシックカーや通貨先物まで、ネットワークを介して
  金銭的価値を持つほぼすべてのものを交換できます。
* `チェーンコード`_ --- チェーンコードの実行は、トランザクションの順序付け、
  ノードタイプ間で必要な信頼と検証のレベルの制限、およびネットワークのスケーラビリティと
  パフォーマンスの最適化から分離されています。
* `台帳機能`_ --- イミュータブルな共有台帳は、各チャネルのトランザクション履歴全体をエンコードし、
  効率的な監査と係争解決のためにSQLに似たクエリ機能を備えています(訳注:台帳は後から第三者が
  参照・検証可能で、干渉したトランザクションがどのように解決されたかチェックできる機能を備えています)。
* `プライバシー`_ --- チャネルとプライベートデータコレクションによって、
  共通のネットワーク上で資産を交換する競合企業や規制された業界が通常必要とする、
  プライベートおよび機密の多組織間のトランザクションが可能になります。
* `セキュリティおよびメンバーシップサービス`_ --- 許可型のメンバーシップは、
  信頼されたブロックチェーンネットワークを提供します。このネットワークでは、
  承認された規制機関や監査機関がすべてのトランザクションを検出し、
  トレースできることが参加者に知らされます。
* `合意形成`_ --- 合意形成に対するユニークなアプローチは、企業にとって
  必要な柔軟性と拡張性をもたらします。

資産
----

資産は、有形資産(不動産およびハードウェア)から無形資産(契約および知的財産)まで多岐にわたります。
Hyperledger Fabricは、チェーンコード取引を使用して資産を変更できます。

資産は、キーと値のペアの集合としてHyperledger Fabricで表現され、状態の変更は、
:ref:`Channel` の台帳上にトランザクションとして記録されます。
資産は、バイナリ形式またはJSON形式、あるいはその両方で表現できます。

チェーンコード
----------------------

チェーンコードは、資産を定義するソフトウェアであり、資産を変更するための取引指示です。
つまり、ビジネスロジックです。チェーンコードは、キーと値のペアまたはその他のステートデータベース情報の
読み取りまたは変更に対して、その規則を強制します。チェーンコード関数は、
台帳の現在のステートデータベースに対して実行され、トランザクション提案を通じて開始されます。
チェーンコードの実行によって作成されるキーと値の書き込みの集合(書き込みセット)は、
ネットワークに送信され、すべてのピアの台帳に適用されます。

台帳機能
---------------

台帳は、 Fabric内のすべての状態遷移に関する、順序付けられた改ざん防止レコードです。
状態遷移は、参加当事者によって提出されたチェーンコード呼び出し('トランザクション')の結果です。
各トランザクションでは、資産に関するキーと値のペアのセットを作成、更新または削除という形で台帳に記録します。

この台帳は、ブロックチェーン('チェーン')で構成され、イミュータブルで順序付けられたレコードを
ブロックに格納します。また、現在の Fabric状態を維持するためのステートデータベースもあります。
チャネルごとに1つの台帳があります。各ピアは、メンバーであるチャネルごとに台帳のコピーを保持します。

Fabric台帳には以下のような機能があります:

- キーベースでの参照、範囲クエリおよび複合キークエリを使用した台帳のクエリおよび更新
- リッチなクエリ言語を使用した読み取り専用クエリ(ステートデータベースとしてCouchDBを使用している場合)
- 読取り専用履歴クエリ --- キーの台帳履歴のクエリにより、データの来歴を追うことが可能
- トランザクションは、チェーンコードで読み取られたキー/値のバージョン(読み取りセット)と
  チェーンコードで書き込まれたキー/値のバージョン(書き込みセット)で構成されます
- トランザクションには、すべてのエンドーシングピアの署名が含まれ、オーダリングサービスに送信されます
- トランザクションはブロック内で順序付けられ、オーダリングサービスからチャネル上のピアに"配信"されます
- ピアは、トランザクションをエンドースメントポリシーと照合して検証し、ポリシーを強制します
- ブロックを追加する前に、バージョンチェックを実行して、読み込まれたアセットの状態が
  チェーンコードの実行時以降に変更されていないことを確認します
- トランザクションが検証されコミットされて、イミュータビリティが生じます
- チャネルの台帳には、ポリシー、アクセスコントロールリスト、他の関連情報を定義する
  コンフィギュレーションブロックが含まれます
- チャネルには :ref:`MSP` インスタンスが含まれ、これにより暗号資料を異なる認証局から取得できます

データベース、ストレージ構造、"クエリ機能"の詳細については、 :doc:`ledger` のトピックを参照してください。

プライバシー
------------

Hyperledger Fabricは、チャネル単位でイミュータブルな台帳を使用するとともに、
資産の現在の状態を操作および変更できるチェーンコード(キーと値のペアを更新)を使用します。
台帳は、チャネルの単位で存在します。台帳は、ネットワーク全体で共有することも
(すべての参加者が1つの共通チャネルで動作していると仮定)、
特定の参加者のセットのみを含めるように私有化することもできます。

後者のシナリオでは、これらの参加者は別のチャネルを作成し、それによってトランザクションと台帳を
隔離/分離します。完全な透過性とプライバシーの間のギャップを埋めたいというシナリオを解決するために、
チェーンコードは、読み取りと書き込みを実行するために資産状態にアクセスする必要があるピアにのみ
インストールできます(つまりチェーンコードがピアにインストールされていない場合、そのピアは
台帳のインターフェースに適切に接続することができません)。

そのチャネル上の組織のサブセットが取引データの機密を保持する必要がある場合、
プライベートデータコレクション(コレクション)を使用して、チャネル台帳から論理的に分離された
プライベートデータベース内にこのデータを分離し、承認された組織のサブセットのみがアクセスできるようにします。

したがって、チャネルは、より広いネットワークからトランザクションをプライベートに保つ一方で、
コレクションは、チャネル上の組織のサブセット間においてデータをプライベートに保ちます。

データをさらに難読化するには、AESなどの一般的な暗号化アルゴリズムを使用して
チェーンコード内の値を(部分的または全体的に)暗号化してから、オーダリングサービスに
トランザクションを送信し、台帳にブロックを追加します。暗号化されたデータは、
台帳に書き込まれた後、暗号テキストの生成に使用された対応するキーを持つユーザーだけが復号できます。

ブロックチェーンネットワークでプライバシーを実現する方法の詳細については、
:doc:`private-data-arch` のトピックを参照してください。

セキュリティおよびメンバーシップサービス
--------------------------------------------------------------------------

Hyperledger Fabricは、すべての参加者が既知のアイデンティティを持つトランザクションネットワークを
サポートします。公開鍵インフラストラクチャは、組織、ネットワークコンポーネント、および
エンドユーザもしくはクライアントアプリケーションに関連付けられた暗号化証明書を生成するために
使用されます。その結果、データアクセス制御は、より広範なネットワークおよびチャネルレベルで
操作および管理できます。Hyperledger Fabricのこの"許可型"概念は、チャネルの存在と機能と相まって、
プライバシーと機密性が最も重要な関心事であるシナリオに対処するのに役立ちます。

詳細は、 :doc:`security_model` のトピックを参照してください。

合意形成
---------

分散台帳技術では、合意形成は単一機能内における特定のアルゴリズムを表す言葉として近年では捉えられています。
しかしながら、合意形成は単にトランザクションの順序に合意するためだけではありません。
Hyperledger Fabricでは、提案およびエンドースメントから、オーダリング、検証およびコミットに至るまで、
トランザクションフロー全体における基本的な役割を通じて、この合意形成の役割の違いが強調されています。
簡単に言うと、コンセンサスは、ブロックを構成する一連のトランザクションの正確さを完全に検証する
一連のプロセスとして定義されます。

ブロックのトランザクションの順序と結果が明示的なポリシー基準のチェックを満たすことによって、
合意形成は最終的に達成されます。これらの抑制と均衡は、トランザクションのライフサイクルの間に行われ、
特定のトランザクションクラスをどの特定のメンバーが承認する必要があるかを決定するための
エンドースメントポリシーの使用と、これらのポリシーが確実に強制および維持されるようにするための
システムチェーンコードを含みます。コミットの前に、ピアは、十分なエンドースメントが存在し、
それらが適切なエンティティから得られたものであることを確認するために、これらのシステムチェーンコードを
利用します。さらに、トランザクションを含むブロックが台帳に追加される前に、台帳の現在の状態が
合意または同意されているバージョンであるかチェックをします。
この最終チェックにより、データの整合性を損なう可能性のある重複支出操作およびその他の脅威から保護され、
静的ではない変数に対して関数を実行できます。

エンドースメントの数、妥当性、バージョン管理のチェックが行われるだけでなく、
トランザクションフローにおけるすべての通信間でアイデンティティの検証が行われています。
アクセスコントロールリストは、(オーダリングサービスからチャネルまでの)ネットワークの階層レイヤで実装され、
トランザクション提案がさまざまなアーキテクチャコンポーネントを通過するときに、
ペイロードが繰り返し署名、検証、および認証されます。結論として、合意形成は、
一連のトランザクションの順序に関して合意する役割に限定されるのではなく、
提案からコミットまでのトランザクションの過程で繰り返し行われる検証の副産物として達成される
包括的な役割を持っています。

合意形成を視覚的に表現するには、 :doc:`txflow` の図を見てください。

.. Licensed under Creative Commons Attribution 4.0 International License
   https://creativecommons.org/licenses/by/4.0/
