# java_bug_list

1、java开发中修改到了目标文件
详情：正常开发过程中都是修改源文件，这次稀里糊涂的修改到了目标文件。
展示规律：开发过程中没有特别的错误，唯一可以表现出异常的情况是，修改mapper文件时，需要clean后才可能生效。最大的问题是，版本库合并代码的时候合不到目标文件中的代码，会导致代码在我机器上跑没问题，在别的地方跑有问题。
解决办法：避免修改目标文件中的代码；



2、数据库大小写不敏感问题

详情：在一个bean的属性设置时，有两个属性字母全相同、大小写不同。

展示规律：在数据库查询数据返回bean类型的数据时，数据库能查询到数据，但是数据注入不到bean里，原因应该是数据库对大小写不敏感，导致把两个值都注入到了同一个属性中，另一个属性获取不到值

解决办法：bean的属性命名一定要用不同的字母区分，不能用大小写区分





