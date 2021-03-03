# ios_bug_list

1、验签类bug
详情：需要验签的接口，如提交评论接口、收藏接口、发票接口等，当上传内容中包含特殊符号（+）时，验签失败。
原因：使用普通post请求提交时，系统会默认转化特殊符号，导致服务端拿到的字符串和客户端拿到的字符串不一样。当然也会导致验签的结果不一样。
解决办法：使用multipart/form-data;的内容类型提交请求



2、编译bug

详情：Xcode12真机可运行，模拟器运行报编译错误：No architectures to compile for (ONLY_ACTIVE_ARCH=YES, active arch=x86_64, VALID_ARCHS=armv7 arm64).

原因：Xcode12淘汰了VALID_ARCHS,但是有些cocoapod集成进来的第三方库还是有这个key,Xcode12模拟器已经用arm架构来编译项目,而link链接的还是x86架构

解决办法：找到Build Settings-VALID_ARCHS在里面添加 x86_64

3、上传ipa包bug
详情：Xcode12打包上传App Store，选择签名文件的前一步提示Xcode的账号不对，查看Xcode的账号又没问题
原因：未明
解决办法：重启Xcode后可成功上传
