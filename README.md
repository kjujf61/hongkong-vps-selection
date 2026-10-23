# 香港vps：三网回程怎么挑，GoMami 香港套餐真实年费与选购判断

香港 VPS 贵和便宜，差的主要在回程线路和晚高峰表现，配置表上的核数和内存反而没那么关键。同样标“2 核 4G”，有的机器大陆访问 40ms 稳定，有的晚八点开始丢包。这篇围绕 GoMami 的香港产品线，把当前能查到的套餐、价格、优惠和几个容易踩的限制摊开算一遍，帮你判断要不要为线路多付这笔钱。

## 选购速览

> 个人建站、轻量 API、代理节点：先看 **HKG.Pulse.Mini**，2 核 4G / 60GB NVMe / 1TB 流量，官网购物车页确认了这套配置。官网首页另有一组 EPYC 7763 的 Mini 档标价 $39/月，与第三方整理的 Pulse Mini $59/月 对不上，下单前以 Configure 页右侧 Order Summary 的金额为准。
> 跑游戏服务器、实时通信、编译这类吃单核的：看 **HKG.Turin.Mini**，2 核 4G / 100GB NVMe / 2Gbps，$69/月，用 EPYC 9575F。
> 需要 Windows：只有 Pulse 的 Pro 和 Ultra 两档在官网购物车页标注了 Windows-ready。

👉 [查看 GoMami 香港套餐当前价格](https://bit.ly/Gomami)

## 香港 VPS 的价格差，到底差在什么地方

差在线路走向、机房互联和硬件代际，不在标称带宽。GoMami 香港节点把三网分开优化：电信 CN2/163、联通 AS9929/4837、移动 CMIN2/CMI。机房在 Equinix HK2，通过 BGP 对等互联直连日本 BBIX Tokyo 和新加坡 Equinix SG1，亚太骨干网是 10G 端口。官方给中国大陆方向的口径是 RTT <50ms。

这套东西的成本是硬的。同样一台 2 核 4G，走国际 BGP 的香港机器可以卖到年付百元级，走三网精品回程的机器月付就要几十美元。所以看到香港 VPS 报价从三位数年付到 $69/月，不用怀疑谁标错了价，它们面向的是两类完全不同的需求。

还有一个常被销售页含糊过去的点：三网优化里的 CN2、AS9929、CMIN2 分属电信、联通、移动三家不同的骨干，多数商家只认真优化其中一家，另外两家靠默认路由凑数。GoMami 在官网套餐页把三线都列为标配（标记为 China Mainland Optimized Pro），不作为付费加项。这一点直接决定非主力运营商的用户会不会在晚高峰被区别对待。

GoMami 香港有三条产品线：

| 产品线 | 定位 | 硬件 | 可用节点 |
| --- | --- | --- | --- |
| Turin | 性能旗舰 | AMD EPYC 9575F（Zen 5）+ PCIe Gen5 SSD + DDR5 6400 | 仅香港 |
| Pulse | 均衡通用 | AMD EPYC 7763，3.5GHz | 香港、日本、新加坡 |
| Forge | 独立服务器，硬件独占 | 定制配置 | 仅香港 |

Forge 属于独立服务器，官网没有公开配置和价格，本文不涉及。

## GoMami 香港全部在售套餐

先看两条件能线的全部档位。Turin 四个档位有两份第三方整理互相印证（2026 年 6 月与 10 月），配置和价格一致；另一条 5.0GHz 以内的 Ryzen 9 9950X 线，官网首页只按处理器标注，未写系列名，一份测评机器的套餐名为 HKG.Peak.X5.Mini，配置价格与官网首页 Ryzen Mini 档完全对得上，下表沿用这个称呼。

| 套餐 | vCPU / 内存 / NVMe | 流量 / 带宽 | 月付价 | 购买 |
| --- | --- | --- | --- | --- |
| HKG.Turin.Mini | 2 核 / 4GB / 100GB | 1000GB / 2Gbps | $69 | [ 选 Turin Mini](https://bit.ly/Gomami) |
| HKG.Turin.Air | 4 核 / 8GB / 140GB | 2000GB / 2Gbps | $129 | [ 选 Turin Air](https://bit.ly/Gomami) |
| HKG.Turin.Pro | 6 核 / 16GB / 180GB | 5000GB / 5Gbps | $299 | [ 选 Turin Pro](https://bit.ly/Gomami) |
| HKG.Turin.Ultra | 12 核 / 32GB / 220GB | 10000GB / 5Gbps | $599 | [ 选 Turin Ultra](https://bit.ly/Gomami) |
| HKG.Peak.X5.Mini | 2 核 / 4GB / 40GB | 1000GB / 2Gbps | $59 | [ 选 Peak X5 Mini](https://bit.ly/Gomami) |
| HKG.Peak.X5.Air | 4 核 / 8GB / 60GB | 2000GB / 2Gbps | $99 | [ 选 Peak X5 Air](https://bit.ly/Gomami) |
| HKG.Peak.X5.Pro | 6 核 / 16GB / 80GB | 5000GB / 5Gbps | $199 | [ 选 Peak X5 Pro](https://bit.ly/Gomami) |

再看 Pulse。官网购物车页确认了 Nano 到 Ultra 五个档位的完整配置，但没有显示价格；下表价格来自 2026 年 10 月的第三方整理。

| 套餐 | vCPU / 内存 / NVMe | 流量 / 带宽 | 月付价（下单页为准） | 购买 |
| --- | --- | --- | --- | --- |
| HKG.Pulse.Nano | 2 核 / 2GB / 40GB | 500GB / 1Gbps | $49 | [ 选 Pulse Nano](https://bit.ly/Gomami) |
| HKG.Pulse.Mini | 2 核 / 4GB / 60GB | 1000GB / 1Gbps | $59 | [ 选 Pulse Mini](https://bit.ly/Gomami) |
| HKG.Pulse.Air | 4 核 / 8GB / 80GB | 2000GB / 1Gbps | $119 | [ 选 Pulse Air](https://bit.ly/Gomami) |
| HKG.Pulse.Pro | 8 核 / 16GB / 100GB | 5000GB / 3Gbps | $269 | [ 选 Pulse Pro](https://bit.ly/Gomami) |
| HKG.Pulse.Ultra | 12 核 / 32GB / 300GB | 10000GB / 3Gbps | $499 | [ 选 Pulse Ultra](https://bit.ly/Gomami) |

价格这块必须留一句提醒。官网首页还并列展示了另一组 EPYC 7763 配置，只标处理器、不标系列名：Mini 2 核 / 4GB / 40GB / 1000GB / 1Gbps 标价 $39，Air 4 核 / 8GB / 60GB / 2000GB / 1Gbps 标价 $79，Pro 8 核 / 16GB / 80GB / 5000GB / 3Gbps 标价 $169。这三档和上表 Pulse 的 Nano / Mini / Pro 起价对不上（$39 对 $49、$79 对 $119、$169 对 $269），硬盘容量也不同，很可能是两套不同的 EPYC 7763 产品，或者 Pulse 在 2026 年年中调过价。**任何表格里的价格都只是参考，最终以 Configure 页 Order Summary 显示的金额为准。**

## Turin、Peak X5、Pulse 怎么选

三者的差别不在“新旧”，而在处理器取向和同价位给的东西。Pulse 用 EPYC 7763，核心数多、频率低，适合并发型负载。另外两条线都是高频单核路线：Turin 用 EPYC 9575F，5.0GHz 加速；Peak X5 用 Ryzen 9 9950X，官方标最高 5.7GHz。一份对 Peak X5 Mini 的独立测评记录显示 Geekbench 6 单核 3419、多核 5974，作者判断 CPU 分数接近裸金属水平，但同时指出该机型的磁盘 IO 相对 7763 系列被砍了一截，顺序读写落在 400–600 MB/s 区间而非 GB 级。

据此可以拆成三条判断：

**单核是瓶颈**（游戏服务器、实时 API、编译）：Turin Mini 或 Peak X5 Mini 都行。同价位上 Turin Mini 多 $10，换来 100GB 而非 40GB 的 NVMe，端口同为 2Gbps，但处理器换成 Zen 5 架构加 PCIe Gen5 SSD。硬盘敏感选 Turin，频率敏感、预算紧选 Peak X5。

**并发是瓶颈**：Pulse Pro 给到 8 核 16G / 100GB / 5TB，$269；Turin Pro 是 6 核 16G / 180GB / 5TB，$299。核数上 Pulse Pro 赢 2 核，硬盘上 Turin Pro 多 80GB，单核性能也是 Turin 更高。跑多容器、数据库连接池、批处理任务，Pulse Pro 更合适；要同时兼顾单核响应和本地存储，才轮到 Turin Pro。

**只要最便宜的入门档**：Pulse Nano 的 2 核 2G / 40GB / 500GB 流量 $49，但它只有 500GB 出向流量，挂个图片稍多的站很容易见底。官网首页那组 $39 的 EPYC 7763 Mini 如果确实在售，流量同样只有 1000GB，性价比更高，值得在下单页确认一遍。

## 一年到底要花多少钱

按月付算，Turin Mini 一年 $828，Peak X5 Mini 一年 $708，Pulse Mini 一年也是 $708。这是不打折的账面数字。

目前与香港 Turin 直接相关、时间最近的优惠是 **GOMAMI365**，2026 年 10 月的整理记录显示香港 HKG Turin 系列年付 8 折。按这个折扣算，Turin Mini 年付从 $828 降到 **$662.40**，一年省 $165.60，等效月付 $55.20，反而低于 Pulse Mini 的月付。

另外两个码要分清：`Hi,LAX` 是洛杉矶 Pulse 系列首发 8 折，与香港无关；`HappyBirthday` 是全套餐折扣码，一份对 Peak X5 Mini 的下单记录显示它把 $59 打到 $50.15（约 85 折），但那是较早的下单，当前是否仍生效、能否与 GOMAMI365 叠加，官网没有说明。

实操路径很清楚：选好套餐，在 Review & Checkout 页面填码，盯着 Order Summary 的金额有没有变，再付款。三个码能不能叠，只能自己在下单页试一次。

👉 [用年付方案开通香港 Turin](https://bit.ly/Gomami)

## 几个会实际影响使用的限制

**流量超限后限速到 20 Kbps。** 这是最需要注意的一条。GoMami 不是超流量停机，而是限速到几乎不可用的程度，一直持续到下个账单周期重置。官网提供流量包加购，可按需加，不必升级整个套餐。Pulse Nano 只有 500GB 流量，Turin Mini 是 1000GB，选档时先按实际出向流量估一遍。

**流量按单向计费。** 只统计出向流量，入向不计。这对下载型、镜像型业务友好，对上传为主的业务没有帮助。

**只有 Pulse Pro 和 Ultra 标了 Windows-ready。** 官网购物车页在这两档上明确标注支持 Windows，其他档位没有这个标记。要装 Windows 的，别从 Nano 或 Mini 起步。

**每日自动备份到 AWS S3。** 两处第三方都提到这个特性，但备份保留多久、能否自助恢复、是否额外收费，官网页面没有说明，下单前值得问一句客服。

**退款窗口 24 小时。** 第三方测评写的是 24 小时内无理由退款。这意味着测延迟、测路由的机会只有一个晚上，建议开通当晚就在晚高峰（北京时间 20:00–23:00）跑一遍。

## 谁不该买 GoMami

预算敏感、流量消耗大、主要用户在欧美的人，买 GoMami 大概率是浪费钱。

香港 VPS 市场有大量更便宜的选项。野草云的香港轻量系列在其公开促销页上标到年付 ¥99 起，续费同价，走国际 BGP 或优质 BGP 网络。这个价位和 GoMami 的月付几十美元差了将近一个数量级，适合博客、测试环境、轻量代理这类对晚高峰不敏感的用途。

主要用户在欧美的，香港节点本身就不是最优解。GoMami 自己的洛杉矶 Pulse 系列 Nano 档 $29/月，是全线最便宜的入口，但资料中没有看到对 GoMami 洛杉矶节点中国大陆延迟的独立实测，这里不做数字推算，只提示一件事：跨太平洋的物理距离摆在那里，别指望和香港同一个体验。

还有一类人容易被“600 Gbps DDoS 防护”吸引但实际用不上。防护是默认尽力而为，可选高级清洗，第三方测评提到 GoMami 的 DDoS 策略偏激进，有时会限制上行带宽。普通企业站被攻击的概率不高，为这个能力付溢价未必划算；真被打过的业务才值得。

## 购买流程，以及容易卡住的两步

1. 登录 GoMami 账户，左侧栏选 HONG KONG，再选 HKG Turin、HKG Pulse 等系列。
2. 在套餐列表点 Order Now，进入 Configure 页面核对规格，选计费周期。官方文档明确提示，更长周期通常价格更好。
3. 右侧 Order Summary 实时显示费用，确认后点 Continue 加入购物车。
4. 在 Review & Checkout 页面核对产品和价格，**这一步填 Promo Code**，然后点 Checkout。
5. 选支付方式：账户余额、信用卡、Stripe 支付宝、加密货币。可填 Additional Notes，勾选同意服务条款，点 Complete Order。
6. 付款后系统自动部署，通常几分钟内完成，IP 和登录凭据会发到邮箱。

两个容易卡住的地方：优惠码在购物车页填，不在最后的 Checkout 页，填完一定要看金额有没有变；部署完成后先到实例面板确认状态，再用 SSH 连接，首次登录用邮箱里的凭据。

## 常见问题

**能先试用再买吗？** 官网 FAQ 列了“能不能先试用”这个问题，但页面没有给出答案。能确认的是第三方测评提到的 24 小时内可退款，一个晚上的窗口够测延迟和路由，不够跑长期稳定性。

**流量用完了会停机吗？** 不会停机，会限速到 20 Kbps 直到下个账单周期。可以提前买流量包，不用换套餐。

**支持支付宝吗？** 官方购买文档列的支付方式包括 Stripe Alipay，即通过 Stripe 用支付宝付款，另有信用卡和加密货币。

**香港、日本、新加坡同配置谁便宜？** Pulse 系列在三个节点用同一套硬件思路，日本和新加坡的 Mini 档 $49、Air 档 $89、Pro 档 $169，比香港同档略低。香港的优势是延迟，日本和新加坡的优势是覆盖范围，按用户位置选。

**IPv6 支持吗？** 资料里没有官网关于 IPv6 的说明，只有一份测评机器的网络栈显示 IPv6 处于离线状态。这条不能当成全线结论，需要 IPv6 的直接在下单前问客服。

## 最后怎么定

个人博客、轻量 API、代理节点，1TB 流量够用 → HKG.Pulse.Mini，先月付跑一个月看晚高峰表现。

游戏服务器、实时通信、编译，单核是瓶颈 → HKG.Turin.Mini（$69，100GB NVMe）或 HKG.Peak.X5.Mini（$59，40GB NVMe），硬盘优先选前者，频率和预算优先选后者。

要多核并发 → HKG.Pulse.Pro，8 核 16G / 100GB，$269；只有在你同时需要更大本地硬盘和更强单核时，才加钱上 Turin Pro 的 6 核 16G / 180GB。

要装 Windows → 只能从 Pulse Pro 或 Pulse Ultra 起。

下单前做两件事：在购物车页把优惠码填进去，确认 Order Summary 的金额确实变了；开通后当晚跑一次延迟和路由测试，24 小时退款窗口内还有反悔的余地。

👉 [去 GoMami 按你的配置下单香港 VPS](https://bit.ly/Gomami)
