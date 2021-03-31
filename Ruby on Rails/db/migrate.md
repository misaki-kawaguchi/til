# マイグレーションに関する主なコマンド

|  コマンド |  意味  |
| ---- | ---- |
|  bin/rails db:migrate  |  最新までマイグレーションを適用する  |
|  bin/rails db:migrate VERSION=20180608051058  |  特定バージョンまでマイグレーションが適用された状態にする。VERSIONにはマイグレーションファイル名の先頭の数字部分（日付部分）を指定する  |
|  bin/rails db:rollback  |  バージョンを1つ戻す |
|  bin/rails db:rollback STEP=2  |  バージョンを指定したステップ数だけ戻す  |
|  bin/rails db:migrare:redo  |  バージョンを1つ戻してから1つ上げる  |
|  bin/rails db:migrate:status  |  migrationの状態を確認する  |
