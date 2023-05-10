- https://www.karakaram.com/notes-on-jq-command/

- jq -Cオプション
- https://stedolan.github.io/jq/manual/

```
kinesis ログ内のアプリログ部分を抽出
cat kinesis_datadog-1-2023-02-10-10-* | jq -r '.logEvents[].message' > a

ERROR レベルログを抽出
cat a | jq '.log_processed.level = "ERROR"' | jq -C | less -R

```


### 標準入出力
- https://www3.cuc.ac.jp/~miyata/classes/prg1/07/stdio.html

### less
- 　「less」は、テキストファイルを1画面ずつ表示するコマンドです
- 　- Rコマンドは、可能な限り画面表示を正しく維持する
- 　https://atmarkit.itmedia.co.jp/ait/articles/1702/10/news022.html
