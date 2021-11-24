# 三个月撸完后的感叹
ql repo https://github.com/photonmang/quantumultX.git "JDscripts"
首次撸满了50元，审核通过后多日未到账，联系小小影视管理员，表示需要升级到最新版本，因提现金额已变更为100元，还表示会退回金币，然后过了三个月也并未退回。
10月20日再次于撸满了100元并提现，在审核通过后还是出现多日不打款。再次联系小小影视管理员，对方表示不能一直靠签到提现，需要邀请用户。但我也有2个邀请用户，并且保持一个日活。再次追问下，小小影视管理不再继续理会。根据这个情况，即使通过邀请方式撸满100元的提现，也有可能被判断为刷单行为，所以继续撸的金币只能用来兑换一些下载及观影权限。是否继续使用，请各位大佬们自行斟酌！

# 小小影视

> 代码已同时兼容 QuantumultX,Surge,Loon,JSBox,Node.js 使用同一份签到脚本即可

> 九合一任务（签到，广告，分享，评论，10次观影，5次收藏，30分钟连续观影，每日22点开宝箱，每周六22点开宝箱）

> 已重构代码，解决多任务一堆提醒，改为签到完成后仅一次提醒。

> 脚本执行时间大概为30多分钟，因包含连续观影的自动执行，所以没有特殊情况请不要手动执行。

> 保留连续观影和其他签到的拆分task脚本。根据喜好自行搭配使用。

## 配置 (QuanX)
```properties
[MITM]

*.xjxjappss.com,*.xjxjapps.com,*.xxjjappss.com,*.xjwdapps.com,*.leleapps.com,*.leyiapps.com,*.hpplay.cn,*.gqbyh.com

[rewrite_local]

# 189及以前版本
^https:\/\/.*\..*\.com\/ucp\/index url script-response-body xxys.cookie.js
# 190及以后版本
^https:\/\/.*\..*\.com\/ucp\/index url script-request-header xxys.cookie.js

[task_local]
#小小影视完整签到配置
0 10,22 * * * https://raw.githubusercontent.com/photonmang/quantumultX/master/xxysrw.js, tag=小小影视, img-url=https://raw.githubusercontent.com/Orz-3/task/master/xxys.png, enabled=true

#小小影视不含连续观影任务
0 10,22 * * * https://raw.githubusercontent.com/photonmang/quantumultX/master/xxys_6rw.js, tag=小小影视, img-url=https://raw.githubusercontent.com/Orz-3/task/master/xxys.png, enabled=true

#小小影视连续观影
*/10 0 10 * * * https://raw.githubusercontent.com/photonmang/quantumultX/master/xxys_play.js, tag=小小影视, img-url=https://raw.githubusercontent.com/Orz-3/task/master/xxys.png, enabled=true
```
## 说明

1. 登陆小小影视APP，点击“我的”，自动获取到cookie，就可以注释获取cookie脚本了


## 常见问题

1. 无法写入 Cookie

   - 请查看配置的mitm是否正确，可以抓包看域名。

2. 写入 Cookie 成功, 但签到不成功

   - 看看是否因为task的任务执行时间错了。

3. 为什么有时成功有时失败

   - 很正常，网络问题，因为执行的时候网络卡一下，跳过了配对时间执行不会生效，尤其是完整版。



