# 集成iOS sdk过程中搜索不到libz.dylib和libstdc++.dylib库

iOS9后 原来的dylib后缀名的库全部修改成了tbd,因此 libz.dylib相当于libz.tdb，libstdc++.dylib 相当于 libstdc++.tdb
如果Link Binary With Libraries中添加的时候 找不到libz.dylib和libstdc++.dylib库，直接搜索对应的libz.tdb和libstdc++.tdb即可。