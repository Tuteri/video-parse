# 🎯 去水印聚合解析 API 调用文档

更多解析接口访问 https://www.douyidou.cc

## 📌 接口地址

```
GET http://gateway.diadi.cn/api/parse
```

浏览器访问测试 https://gateway.diadi.cn/api/parse?app_secret=1xoHycbECYHIqoMcrtvYvXOuVHCjEczJv&url=https%3A%2F%2Fv.douyin.com%2Fp1G164ZIlXU%2F

------

## 🔐 请求参数

| 参数名       | 类型   | 是否必须 | 说明                                |
| ------------ | ------ | -------- | ----------------------------------- |
| `app_secret` | string | 是       | 授权密钥（请妥善保管）              |
| `url`        | string | 是       | 要解析的视频分享链接（需 URL 编码） |



------

## 🚀 请求示例

**原始链接：**

```
https://v.douyin.com/p1G164ZIlXU/
```

**URL 编码后：**

```
https%3A%2F%2Fv.douyin.com%2Fp1G164ZIlXU%2F
```

**最终请求：**

```
https://gateway.diadi.cn/api/parse?app_secret=5HkBIAwYnpzfzbnjsdtGmfAryDWXPBiKk&url=https%3A%2F%2Fv.douyin.com%2Fp1G164ZIlXU%2F
```

------

## 🔄 返回格式（JSON）

成功返回示例：

```json
{
  "code": 0,
  "data": {
    "video": [
      "https://v5-small.douyinvod.com/97241a67059f141d553c66f078df0f81/683e92b6/video/tos/cn/tos-cn-ve-15/oAf7GQpIGePGXCxsAIeOAtgjqLrdWNBBtCg7c2/?a=1128&ch=0&cr=0&dr=0&er=0&cd=0%7C0%7C0%7C0&cv=1&br=2584&bt=2584&cs=0&ds=4&ft=LjhJkw998xI7uEPmD0P5NdvaUFiXxrUfRVJEX6zAVbPD-Ipz&mime_type=video_mp4&qs=0&rc=aGU4OGU2aGdnNzZmOTY5OkBpM3B3Z2o5cm9ldTMzNGkzM0BjLjMyYGMxXi4xMzUyLzEtYSM1Xm9pMmQ0ZW9gLS1kLTBzcw%3D%3D&btag=c0000e0009d000&cquery=100y&dy_q=1748927619&feature_id=46a7bb47b4fd1280f3d3825bf2b29388&l=20250603131339399DF70B5CB81D90D982"
    ],
    "images": [],
    "cover": "https://p3-pc-sign.douyinpic.com/image-cut-tos-priv/9cc5e7d8aeac8a94ad957278d05d7af5~tplv-dy-resize-origshort-autoq-75:330.jpeg?lk3s=138a59ce&x-expires=2064286800&x-signature=wE998x42Hwe5hBii1jV4%2Bz%2Bmg0Q%3D&from=327834062&s=PackSourceEnum_AWEME_DETAIL&se=false&sc=cover&biz_tag=pcweb_cover&l=20250603131339C41C864C5DE150828FFC",
    "type": "video",
    "text": "无人扶我青云志，我自踏雪至山巅！#听泉鉴宝直播回放 #听泉鉴宝 #国博文物总店听泉 @听泉鉴宝 @国博文物总店",
    "audio": [
      "https://sf5-hl-cdn-tos.douyinstatic.com/obj/ies-music/7419320683269819190.mp3"
    ],
    "platform": 1,
    "id": "7419320667310492928",
    "author": {
      "nickname": "听泉赏宝（泉哥迷妹～）",
      "id": "MS4wLjABAAAAJKw8tyfjGe9S41ZBsEUFR69O35E5t1nVMdmakLypJx3mcKRgVthsw1nHz_9ImS1k"
    },
    "other": {
      "create_time": 1727445213,
      "comment_count": 554,
      "digg_count": 18339,
      "collect_count": 6181,
      "share_count": 21021
    }
  },
  "message": "ok"
}
```

失败返回示例：

```json
{
  "code": 50001,
  "data": null,
  "message": "解析失败"
}
```

### 📄  基础响应结构

| 参数名称  | 类型   | 描述                  |
| --------- | ------ | --------------------- |
| `code`    | int    | 状态码，0 表示成功    |
| `message` | string | 错误信息，ok 表示成功 |
| `data`    | object | 解析结果数据结构      |

### 📄 `data` 字段结构

| 参数名称   | 类型   | 描述                                             |
| ---------- | ------ | ------------------------------------------------ |
| `type`     | string | 类型，如 `"video"`、`"note"` 等                  |
| `video`    | array  | 视频链接列表                                     |
| `images`   | array  | 图集链接列表                                     |
| `audio`    | array  | 音频链接列表                                     |
| `cover`    | string | 封面图片链接                                     |
| `text`     | string | 视频或图文的文案                                 |
| `platform` | int    | 平台标识符，`1` 表示抖音                         |
| `id`       | string | 内容唯一标识，仅 `platform=1` 时有效             |
| `author`   | object | 作者信息，仅 `platform=1` 时有效                 |
| `other`    | object | 附加信息，如点赞、评论等，仅 `platform=1` 时有效 |

## ✅ 支持的域名列表

```
v.douyin.com
www.douyin.com
m.douyin.com
iesdouyin.com
kuaishou.com
m.chenzhongtech.com
m.kuai-fei.com
pipix
weibo.com
m.weibo.cn
weishi
b23.tv
bilibili.com
pipigx
xhslink.com
www.xiaohongshu.com
xiaochuankeji.cn
soulsmile.cn
oasis.weibo.cn
ixigua.com
haokan.baidu.com
acfun.cn
immomo.com
xinpianchang.com
kg.qq.com
meipai.com
xiaodutv.com
mercury-sdk.snssdk.com
toutiao.com
qishui.douyin.com
music.douyin.com
y.qq.com
boc.inke.cn
newsa.html5.qq.com
ur.alipay.com
sharecontent.lepudding.com
xsj.qq.com
m.eyepetizer.net
jimeng.jianying.com
oceanengine.com
tiktok.com
x.com
t.co
twitter.com
youtube.com
youtu.be
facebook.com
instagram.com
```

------

## 📌 注意事项

1. `url` 参数必须进行 URL 编码，否则接口可能无法正确解析。
2. 支持的平台不限于抖音，建议自行测试其他平台链接是否兼容。

