# 学習ログ

新しい日付を **上に** 足していきます。

---

## テンプレート（コピーして使う）

```markdown
## YYYY-MM-DD

- **やったこと**:
- **理解したこと**:
- **次やること**（任意）:
```

---

## 2026-05-18

- **やったこと**: Laravel 製タスク CRUD（[CRUD](https://github.com/furuyaaaa/CRUD)）の **コアとなるコードの置き場所** を整理し、ルーティング・コントローラ・モデル・マイグレーション・ビューの対応を確認した。学習メモを本リポジトリの `LEARNING_LOG.md` に追記した。

- **理解したこと**:
  - **ルート** … `routes/web.php`（`Route::resource('tasks', ...)` やレポート用ルート）
  - **HTTP 層** … `app/Http/Controllers/TaskController.php`
  - **モデル** … `app/Models/Task.php`
  - **DB スキーマ** … `database/migrations/*_create_tasks_table.php`
  - **画面** … `resources/views/tasks/`（`index` / `create` / `edit` / `report`）
  - **認証** … `routes/auth.php` と `app/Http/Controllers/Auth/`。**プロフィール** … `ProfileController` と `resources/views/profile/`

- **次やること**（任意）: ルートモデル結合・FormRequest・Policy など、続きのレイヤーをコードで追う

## 2026-05-15

- **① DIコンテナ**  
  必要なクラスを `ServiceProvider` で登録しておくことで、コンストラクタに型を書くだけで自動でインスタンスを作って注入してくれる仕組み。

- **② ServiceProvider**  
  Laravel が起動するときに DI コンテナにサービスを登録する場所。`bind()` は毎回新しいインスタンスを作り、`singleton()` は 1 つだけ作って使い回す。

- **③ Closure オブジェクト**  
  無名関数をオブジェクトとして扱えるようにしたもの。変数に入れたり引数に渡したり戻り値として返せる「持ち運びできる関数」。

- **④ `Pipeline.php` の仕組み**  
  `send()`・`through()`・`via()`・`then()` をメソッドチェーンで繋げて、リクエストをミドルウェアに順番に通し、最終的にコントローラーへ届ける仕組み。

- **⑤ メソッドチェーン**  
  `return $this` で自分自身を返すことで、メソッドを数珠つなぎに呼び出せる仕組み。`@return $this` で見分けられる。

- **⑥ `$next` の正体**  
  `Pipeline.php` の `carry()` で組み立てたクロージャが、ミドルウェア（例: `Authorize.php`）の `handle()` に渡される `$next` と対応しており、引数の順番が一致するため同じ流れとして繋がる。

## 2026-05-14

- **やったこと**: プロフィール用リポジトリをローカルにクローンし、学習ログ用ファイルを用意した
- **理解したこと**: プロフィール README と日記を分けると運用しやすい
- **次やること**（任意）:
