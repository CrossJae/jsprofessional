# 第二十一章 Ajax与Comet

## XMLHttpRequest 2级
1. FormData
    * 现代web应用中频繁使用的一项功能就是表单数据的序列化
    * formdata就是为了序列化表单、创建与表单格式相同的数据提供了便利
    * 表单数据的MIME类型`application/x-www-form-urlencoded`
2. 超时设定`timeout`, **只有ie8支持**
    * 请求等待多少毫秒之后停止
    * `xhr.timeout = 1000` 1秒钟
    * 会被`ontimeout`事件处理 `xhr.ontimeout = function(){...}`
3. overrideMimeType()

*-end-*
