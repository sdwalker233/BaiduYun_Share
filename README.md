# BaiduYun_Share
百度云分享功能api（Python3）

关于百度云的api，已经有很多做的很好的项目，例如使用[PCS api](https://developer.baidu.com/wiki/index.php?title=docs/pcs/rest/file_data_apis_list)的[bypy](https://github.com/houtianze/bypy)和[BaiduPCS](https://github.com/mozillazg/baidu-pcs-python-sdk)，使用百度网盘api的[baidupcsapi](https://github.com/ly0/baidupcsapi)，都可以轻松地实现文件操作、下载上传等功能。

因为PCS不提供分享接口，模拟登陆又会出现许多问题（验证码、弹窗等），所以本项目对两种api进行结合，提供一些关于分享的功能，算是对已有项目的补充。

###具体功能：
- 分享文件 `share`
- 列出所有分享 `list_share`
- 取消分享 `cancel_share`

###用法
**使用本项目需有百度云的`access_token`。如果没有，参考[`bypy`](https://github.com/houtianze/bypy)，请先安装`bypy`，在命令行输入`bypy info`并进行授权，接着在`~/.bypy/bypy.json`中找到`access_token`供api使用。**

```
import BaiduYun_Share
access_token = '1.54be391000a16ee6a21791d4a8ea04fe.86400.1331206383.67272939-188383'
bys = BaiduYun_Share.BYS(access_token)

response = bys.share(['/apps/bypy/a'])  #分享/apps/bypy/a
shareid = response['shareid']  #获取分享id
print(response)

response = bys.list_share()  #列出分享
print(response)

response = bys.cancel_share([shareid])  #取消分享
print(response)
```