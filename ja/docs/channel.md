# チャンネル

コントローラーは `#channel` メソッドを持っていて、それを使うことでバックエンドへの接続の状態を知ることができます。チャンネルのアクセスメソッドはリアクティブであるため、状態が変わったときには監視中の評価が再度トリガーされます。利用できるメソッドは以下の通りとなります:

| メソッド    | 詳細                                               |
|-------------|-----------------------------------------------------------|
| connected?  | バックエンドに接続されていれば true となる                    |
| status      | これらのいずれかの値となる :opening, :open, :closed, :reconnecting  |
| error       | 最後に失敗した接続のエラーメッセージ         |
| retry_count | 再接続を試行した回数 (成功した接続は除く)|
| reconnect_interval | 次に再接続を試行するまでの時間 (秒) |

## チャンネルイベント

クライアントが「サーバーに接続したとき」または「サーバーから切断したとき」に処理を実行したい場合があるでしょう。その場合、クライアントのコントローラーで以下のようにすることができます:

```ruby
channel.on('connect') do
  .. connected ..
end

channel.on('disconnect') do
  .. disconnect ..
end
```
