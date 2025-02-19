# 系统限制

本节介绍使用StarRocks系统时需要注意的事项。

1. StarRocks采用MySQL协议进行通信，用户可通过MySQL Client或者JDBC连接到StarRocks集群。选择MySQL Client版本时建议采用5.1之后的版本，因为5.1之前不能支持长度超过16个字符的用户名。
2. 对集群名、数据库名、表名、列名、分区名、用户名、角色名等的要求：
    * 这些名字只能由数字(0-9)、字母(a-z或A-Z)，以及下划线(\_)组成。
    * 名字的长度不能超过64字符。
    * 集群名、数据库名、表名、分区名、用户名，以及角色名均只能以小写或大写字母开头。
    * 列名可以下划线字符开头。
    * 数据库名、表名是区分大小写的，列名字不区分大小写。
3. 对标签（Label）名字的要求：
    导入数据时可指定任务的标签（Label）。标签名字可由下划线(\_)、大小写字母（a-z或A-Z），以及数字(0-9)组成，且长度不能超过128个字符。标签名对起始字符无要求。
4. 建表时，Key列不能用Float或者Double类型，可用Decimal类型表示小数。
5. VARCHAR最大长度可为65533字节.
   > 65535（行最大值）- 2（长度标识位，记录实际数据长度）= 65533 。
6. StarRocks只支持UTF8编码，不支持GBK等编码。
7. StarRocks不支持修改表中的列名。
8. 一个表达式孩子的最大个数默认为 10000，比如 in 条件的个数，可以通过 fe.conf 的 expr\_children\_limit 修改。
