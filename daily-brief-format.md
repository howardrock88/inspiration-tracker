# 行业早报生成规范

> 生成早报前请先阅读本文档

---

## 生成步骤 (生成前必读)

- [ ] 1. **读取本文档** - 确认格式和搜索策略
- [ ] 2. **读取新闻源列表** - `/Users/yuxiao/.openclaw/workspace/news-sources.md`
- [ ] 3. **确定日期** - 今日日期，用于标题
- [ ] 4. **搜索新闻** - 使用 Brave API，多轮搜索覆盖中英文关键词
- [ ] 5. **筛选过滤** - **只保留前一天新闻(2月17日早报只收录2月16日发布的新闻)**
- [ ] 5.1 读取前一天早报查重
- [ ] 5.2 **手动检查每条新闻的发布日期，排除任何超过24小时的新闻**
- [ ] 6. **分类整理** - 按5大分类整理
- [ ] 7. **检查格式** - 每条新闻必须有简介(50-100字)+原文链接
- [ ] 8. **输出早报** - 发送给人

## 格式模板

```markdown
## 📰 {日期} 行业早报

---

### 🔥 今日焦点

**{新闻标题}**
{新闻简介（50-100字）}
来源: {媒体名称} | {原文链接}

---

### 💰 融资动态

**{公司名}** - {融资金额}
- 投资方: {投资方}
- 简介: {一句话简介}
来源: {媒体名称} | {原文链接}

---

### 🤖 机器人进展

**{新闻标题}**
{新闻简介（50-100字）}
来源: {媒体名称} | {原文链接}

---

### 📊 行业数据

**{标题}**
{数据简介（50-100字）}
来源: {媒体名称} | {原文链接}

---

### 📱 大模型动态

- **{模型/公司}**: {动态简介}
  来源: {媒体名称} | {原文链接}

---

*新闻来源: Brave Search API (90+ RSS源)*
```

## 新闻分类

1. **今日焦点** - 最重要的大新闻，1-2条
2. **融资动态** - AI/科技公司融资，表格形式
3. **机器人进展** - 人形机器人、硬件突破
4. **行业数据** - 市场报告、统计数据
5. **大模型动态** - OpenAI/Anthropic/Google 等大模型更新

## 写作要求

1. 每条新闻必须有**简介（50-100字）**和**原文链接**
2. 链接格式：`来源: {媒体} | {URL}`
3. 标题要简洁有力
4. 重点新闻可以适当详细
5. **只保留前一天的新闻**（例如：2月17日早报只收录2月16日的新闻）

## 搜索策略

### 三大信息来源（必须全部覆盖）

#### 1. Web Search (Brave API)
- 使用 Brave Search API，`freshness: "pd"` 过滤过去24小时
- 中英文双语搜索
- 关键词：AI、机器人、人形机器人、AI硬件、GPU

#### 2. RSS 订阅源
- 运行脚本：`python3 ~/new/rss-monitor-v2.py`
- 获取过去24小时内的最新文章
- 筛选与AI、机器人、科技相关的内容

#### 3. X/Twitter 动态
- 运行脚本或手动搜索
- 关注账号列表：`~/new/x-monitor-accounts.md`
- 搜索格式：`from:OpenAI from:nvidia from:FigureRobot`
- 重点关注：Sam Altman、Sundar Pichai、Elon Musk、黄仁勋等CEO账号

### 合并去重
1. 从三个来源收集新闻
2. 合并去重（相同内容只保留一个来源）
3. 筛选与AI、机器人、AI硬件相关的新闻
4. 只保留前一天(24小时内)发布的新闻

### 新闻源优先级（共90+源）

#### 中文科技媒体 (20)
- 36氪、36氪出海、虎嗅、虎嗅Pro、爱范儿、少数派、钛媒体、钛媒体App、极客公园、PingWest品玩、机器之心、量子位、智东西、雷科技、亿欧、汽车之心、芯东西、新智元、超神经、赛博汽车

#### 中文门户科技 (8)
- 新浪科技、网易科技、腾讯科技、搜狐科技、凤凰网科技、中华网科技、ZOL中关村在线、天极网

#### 中文官媒科技 (6)
- 人民网科技、新华网科技、央视网科技、澎湃科技、光明网科技、中国日报网科技

#### 中文垂直媒体/社区 (12)
- CSDN、InfoQ、SegmentFault、知乎、B站科技区、虎扑科技、抽屉新热榜、观察者网、极客时间、AppSo、科技日报、创头条

#### 中文其他 (6)
- 第一财经Yicai、财新TMT、中国证券报、证券日报IT、每日经济新闻科技、 经济观察报TMT

#### 英文科技媒体 (35)
- TechCrunch、TechCrunch RSS、Wired、The Verge、Ars Technica、Engadget、Mashable、The Next Web、ZDNet、CNET、Digital Trends、Tom's Guide、PCMag、ExtremeTech、IEEE Spectrum、MIT Technology Review、Quartz、The Information、Axios Tech、VentureBeat、TechRadar、TechPP、TechHive、MacRumors、9to5Mac、Android Central、iMore、Wareable、TechAdvisor、Laptop Mag、PCWorld、Computerworld、Network World、InfoWorld

#### 英文门户/通讯社 (18)
- Reuters Tech、BBC Tech、NYTimes Tech、The Guardian Tech、Washington Post Tech、Financial Times Tech、Wall Street Journal Tech、Bloomberg Tech、CNBC Tech、ABC News Tech、CNN Tech、NBC News Tech、Forbes Tech、Fortune Tech、Business Insider Tech、USA Today Tech、MarketWatch Tech、PR Newswire Tech

#### 英文AI/科技垂直 (15)
- Hacker News、TechRadar、LiveScience、ScienceDaily AI、VentureBeat AI、AI News、Artificial Intelligence Weekly、The Robot Report、OpenAI Blog、Google AI Blog、Anthropic Blog、Microsoft AI Blog、NVIDIA Newsroom、DeepMind Blog、MIT News AI

#### 英文科技播客/通讯 (5)
- Lex Fridman Podcast、AI Joe Rogan、The TWIML AI Podcast、Stratechery、 Benedict Evans

#### X/Twitter 热点
- 通过 Brave 搜索获取 AI 行业热门讨论

---
**新闻源总计: 125+**
- 通过 Brave 搜索获取 AI 行业热门讨论
