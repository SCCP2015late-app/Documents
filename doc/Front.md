BurningChatフロントドキュメント

###Angular.js
Angularは画面上のコンテンツをいくつかにグループ分けして制御している。
BurningChatの場合は、左のオレンジ色のパネル（Navigation Panel）右のメッセージリスト（Time Line）右下の入力フォーム（Mention Form）に分割している。
その分割したある一つに対して、コンテンツの制御を行うものをControllerと呼ぶ。Controller同士は基本的にデータのやり取りはできない（と思う）。
このControllerはcontents.jsに定義してある。

###AppEnvironment
Scala.jsのAppEnvironment.scalaにグローバルスコープのオブジェクトを定義してバックエンド、フロントエンドで共有する。
（本当はあまり使うべきじゃないっぽいけど許して）

###リスナーとコールバックについて

ListenerクラスはUIイベント（ボタンのクリックなど）やバックエンドのイベント（メッセージと受信したなど）が起きた時に発火させるコールバックを登録したり呼び出したりするためのクラス。
定義はScala.jsのEventListener.scalaにある。

EventListener
 - addCallback(js.Function1[js.Any, js.Any]): コールバックを登録する。コールバックの引数は一つでなければならない。
 - callAllCallback(): 登録したコールバックを登録した順に全て呼び出す。

EventListenerクラスのインスタンスはAppEnvironment.scalaに定義してある。
ここにリスナーを追加していくことでアプリ全体で利用できるリスナーが増える。
