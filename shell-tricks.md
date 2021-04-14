# shell 使用小技巧

### 去掉数字前面多余的0
`command | sed -r 's/0*([0-9])/\1/'`
如 007820 -> 7820
```shell
str="007820"
str_new=$(echo $str | sed -r 's/0*([0-9])/\1/')
echo $str_new
```
