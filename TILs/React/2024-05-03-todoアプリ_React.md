# Todoアプリ作成(React)

## 1. JSXで構造を作成

## 2. CSSでマークアップ

- jsx内でclass名をつけようとすると、JavaScriptのclassが付与されてしまう
  - classNameを使うこと

## 3. Reactを意識したモックを作成

- stateで定義できそうな部分を意識してみる
  - (例)Todoの一覧
- 配列で定義したら、mapで取り出す
  - 一番最初の要素に`key`を設定すること
  - 再レンダリング時に要素を特定するために必要

## 4. タスクの追加

- テキストの入力値もstateとして保存する
  - `value={todoText}`
  - ただ、このままだと入力しても値が反映されず、初期状態のまま画面が変化しない
- 入力に応じてstateの更新が必要 -> `onChange`
  - onChangeは変更を検知するとeventというオブジェクトを渡す
  - テキストボックスの入力値を取得したい場合は`event.target.value`から取得できる
- これらの処理はフォームライブラリを使って行うことが多い(ReactHookForm)

## 5. タスクの削除

- {}内で関数を呼び出す際、`func()`のように()をつけてしまうと、その部分を通過するたびに関数が実行されてしまう
  - アロー関数を使って関数を生成する
  - `() => onClickDelete(index)`
- 配列を変更する際は**一旦別の変数にコピー**する
  - set関数が実行されたときに、元の配列から変更されていれば更新処理が実施される
  - 直接元の配列を変更すると、変更なしとなり更新処理が行われないので注意
- 削除はspliceメソッドを利用する
  - 第一引数：対象のインデックス
  - 第二引数：対象のインデックスから何個削除するか

## 6. コンポーネント化
- 親でStateや関数を定義して、子には関数をpropsで渡すと、propsの数が少なくなって管理しやすくなる


## JSとの比較

- 生のJSでは記述的にDOM操作を行う
  - すべての行を読まないとどのような画面になるかがイメージしずらい
- Reactは宣言的にDOM操作
  - 特定の場所を読むだけで動作や全体像がイメージしやすい
