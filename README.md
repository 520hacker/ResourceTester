# ResourceTester
看到一个资源的地址，命名很有规则，是不是就可以测试出来这个站点的其他资源在哪？

# 思路如下
http://***/zy/0517/15.m3u8 看起来就是日期+index 的一个资源堆叠方式
其规则如下
- http://***/zy/{1}{2}/{3}.m3u8

那就只需要设计一个程序  把资源可能出现的地址都踩一次 就知道具体的资源是怎么存放的了。

# 看起来不复杂，随手写个代码，使用说明如下：

- 执行程序
- 请提供一个开始猜资源的地址
  - 这个地址需要自己做好规则过滤，目前支持 {0}=年,{1}=月，{2}=日，{3}=每日重置索引
- 请提供一个下载路径,接受默认值 C:\Download 请输入Y
  - 下载路径没做文件夹存在不存在检查，所以务必保证这个文件夹存在
- 请提供一个截止日期,接受默认值 " + DateTime.Now.ToString("yyyy-MM-dd") + " 请输入Y
- 请提供一个单日循环数量,接受默认值 100 请输入Y
  - 默认100 你可以先设置为1，跑一下资源大概在哪些日期，再改成大一点的数
- 等待程序执行完成
- 打开你设置的下载路径 看看都有啥

## 于是 ...

![https://bafybeidj6thjfy7aeqgl26ht36jlptvbp25bvszcujkppwidrlpidnoori.ipfs.dweb.link/](https://bafybeidj6thjfy7aeqgl26ht36jlptvbp25bvszcujkppwidrlpidnoori.ipfs.dweb.link/)

本次是测试的一个M3U8格式的资源， M3U8 文件不一定在本地就能播放，部分能，部分不能，取决于内部是用的相对路径还是绝对路径；本人使用的是 VLC 播放器。 
