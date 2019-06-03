普通に使うと、以下のようなインデックスの絡むサイズが大きすぎるというエラーがでる。

```
Mysql2::Error: Index column size too large. The maximum column size is 767 bytes.
```

そのため、Rails と MySQL 側で以下のような設定をしてやる。

### MySQL

```
[mysqld]
innodb_file_format = Barracuda
innodb_file_per_table = 1
innodb_large_prefix = 1
```

## Rails
`ROW_FORMAT` を `DYNAMIC` にしないと前述の MySQL の設定を使用しないため、
create_table する際に、`ROW_FORMAT=DYNAMIC` を指定する。
