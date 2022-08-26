# open-domain-triple-extract-dataset
# 伪-开放域三元组抽取数据集  
由于某个需求，笔者需要构建一个开放域知识图谱，但网上没找到相关数据集。于是笔者决定把现有的三元组抽取相关数据集都收集起来，正所谓当你关系够多的时候那你就相当于开放域。  
并且笔者根据自己的需求对数据集提出两点要求：1.数据集中所有的文本都能抽出三元组，2.三元组头尾实体都能在数据集文本中找到。  
通过对网上的数据集整理清洗并且加上一部分笔者标注的数据后，我们清洗出了该数据集。其中训练集10573条，验证集300条，测试集462条。  

```python
#打开文件的代码  
with open(filename, encoding='utf-8') as f:  
    D=eval(json.loads(f.readline()))
#下面是关于数据集中关系及其对应的三元组数量
{'主演': 50, '目': 50, '身高': 50, '出生日期': 50, '国籍': 50, '连载网站': 50, '作者': 50, '时间': 1, '歌手': 50, '海拔': 50, '出生地': 50, '导演': 50, '气候': 50, '朝代': 50, '妻子': 50, '丈夫': 50, '民族': 50, '毕业院校': 50, '编剧': 50, '出品公司': 50, '父亲': 50, '出版社': 50, '作词': 50, '作曲': 50, '母亲': 50, '成立日期': 50, '字': 50, '号': 50, '所属专辑': 50, '所在城市': 50, '总部地点': 50, '主持人': 50, '上映时间': 50, '首都': 50, '创始人': 50, '祖籍': 50, '改编自': 22, '注册资本': 50, '人口数量': 50, '面积': 50, '主角': 50, '占地面积': 50, '嘉宾': 50, '简称': 50, '董事长': 50, '制片人': 50, '官方语言': 50, '邮政编码': 49, '专业代码': 39, '修业年限': 33, '风险评估因素': 50, '药物治疗': 50, '并发症': 50, '病因': 50, '辅助治疗': 50, '同义词': 50, '遗传因素': 34, '发病机制': 33, '临床表现': 50, '辅助检查': 50, '发病年龄': 50, '病理分型': 50, '多发群体': 50, '实验室检查': 50, '传播途径': 24, '预后状况': 50, '鉴别诊断': 50, '相关（导致）': 50, '发病率': 50, '手术治疗': 50, '多发季节': 12, '影像学检查': 50, '发病部位': 50, '放射治疗': 45, '阶段': 50, '相关（症状）': 50, '相关（转化）': 50, '组织学检查': 50, '预防': 50, '高危因素': 50, '死亡率': 20, '化疗': 49, '就诊科室': 7, '病史': 40, '病理生理': 18, '多发地区': 50, '转移部位': 50, '筛查': 20, '发病性别倾向': 41, '内窥镜检查': 50, '外侵部位': 34, '治疗后症状': 50, '侵及周围组织转移的症状': 14, '预后生存率': 25, '单位': 21, '组成': 5, '启动': 50, '发布': 50, '举行': 50, '开发': 15, '接受': 50, '确认': 2, '分析': 16, '参与': 50, '开展': 50, '离开': 50, '开始': 3, '作出': 50, '恢复': 50, '地点': 247, '检查': 21, '售出': 1, '设立': 44, '生产': 7, '叮嘱': 1, '增长': 8, '完成': 7, '召开': 50, '选择': 30, '增加': 39, '提出': 50, '开通': 7, '关闭': 2, '推动': 24, '引领': 3, '建立': 50, '推进': 21, '创造': 17, '推出': 50, '举办': 34, '制定': 46, '收购': 50, '成立': 50, '拿出': 3, '支持': 50, '重视': 1, '披露': 23, '达': 3, '解除': 8, '涵盖': 1, '组建': 3, '发行': 37, '晚于': 1, '行政拘留5天': 1, '实现': 5, '影响': 15, '投入': 22, '关注': 29, '解决': 22, '购买': 33, '公布': 50, '暂停购买': 1, '驾驶': 7, '出任': 50, '宣布': 15, '指出': 35, '发出': 11, '转入': 39, '出席': 50, '分享': 24, '做出': 32, '提供': 47, '通报': 43, '研发': 6, '印发': 50, '介绍': 32, '报道': 22, '发表': 50, '参加': 50, '发现': 50, '建成': 11, '会见': 50, '应对': 1, '提高': 10, '纳入': 4, '推荐': 12, '抵达': 3, '致电': 6, '发生': 50, '致慰问电': 1, '暴发': 2, '进行': 8, '邀请': 2, '通电话': 1, '减少': 17, '打造': 15, '自创': 1, '组织': 50, '开放': 13, '促进': 1, '经历': 2, '给予': 21, '履行': 2, '要求': 3, '联手': 1, '告诉': 17, '考察': 1, '督促': 1, '开工': 1, '安排': 4, '到达': 50, '找到': 50, '建议': 12, '制作': 10, '骗取': 1, '吸引': 9, '派遣': 2, '承担': 2, '出台': 7, '搭乘': 1, '投资': 7, '评价': 5, '调查': 23, '体验': 2, '吃': 2, '执行': 27, '开始推进': 1, '调整': 15, '测试': 3, '开启': 21, '导致': 27, '遭受': 1, '直播': 1, '变得': 3, '控制': 21, '提高到': 2, '加大': 2, '带来': 20, '提供团体意外保险': 1, '批准': 33, '总结': 1, '留在': 1, '创建': 2, '放弃': 2, '训练': 2, '撰写': 2, '提升': 4, '去': 1, '移送': 5, '击打': 1, '决定': 1, '执法检查': 1, '接到': 7, '运抵': 1, '涉嫌': 5, '落实': 5, '分离': 1, '检测': 3, '设计': 5, '监测': 1, '通过': 9, '抬高': 1, '日产': 1, '增强': 5, '展现': 1, '打伤': 3, '打开': 4, '涨到': 1, '征集': 1, '曾用': 1, '培养': 0, '学习': 11, '改造': 2, '制订': 2, '利用': 5, '形成': 30, '拿到': 1, '发起成立': 1, '提交': 1, '加强': 2, '负责': 3, '处理': 14, '造成': 3, '穿过': 1, '换乘': 1, '建设': 12, '明确': 2, '按期': 1, '强调': 2, '占据': 1, '发起': 3, '实施': 11, '曝光': 5, '提及': 1, '起诉': 50, '指使': 1, '买了': 1, '发展': 6, '下发': 4, '务工': 1, '指导': 2, '发挥': 0, '查房': 1, '违反': 6, '支付': 8, '引入': 3, '发来': 1, '覆盖': 1, '监管': 1, '不断': 1, '推开': 1, '安装': 1, '创立': 3, '发明': 1, '拍摄': 5, '补充': 4, '上市': 50, '走访': 2, '得益': 1, '试点': 1, '扩大': 1, '申请': 25, '伤害': 1, '被告知': 1, '步入': 1, '施工': 2, '有': 2, '跟着': 1, '带动': 1, '正在研发': 1, '新增': 3, '推广': 1, '被罚': 31, '创下': 1, '污染': 1, '到': 4, '整改': 1, '对': 2, '长期非法': 1, '升级': 3, '再度调整': 1, '回国': 0, '下跌': 13, '成为': 2, '同步跟进': 1, '砍了': 1, '签署': 3, '来到': 9, '辞退': 8, '推介': 1, '走过': 1, '起点': 1, '达到': 2, '开设': 1, '报送': 1, '签订': 1, '被申请': 1, '主动': 1, '拍摄到': 1, '下架': 50, '赴': 3, '诬陷': 1, '开除': 16, '制定并印发': 1, '投诉': 2, '增持': 1, '收到': 3, '出现': 9, '调集': 3, '前往': 5, '排除': 1, '呈现': 1, '延续': 1, '变成': 2, '认定': 1, '首次提出': 1, '增设': 1, '查出': 1, '到账': 1, '审批': 2, '取证分析': 1, '取得': 1, '创作': 1, '查处': 2, '研究解决': 1, '入驻': 4, '修订通过': 1, '免费代理': 1, '融入': 1, '构建': 6, '年增长': 1, '给了': 1, '上调': 8, '了解': 1, '奏响': 1, '自主开发': 1, '量身定制': 1, '扩展到': 1, '培育': 1, '改变': 21, '侦破': 1, '收藏': 1, '减少到': 1, '铲除': 1, '聘请': 1, '采用': 4, '采取': 4, '交流': 3, '宣读': 1, '上线': 50, '加入': 25, '出镜': 1, '采集': 4, '开辟': 1, '帮助': 1, '移交至': 1, '从事': 1, '感谢': 44, '带领': 1, '结束': 7, '检查并记录': 1, '住在': 1, '呈': 2, '主持': 3, '接纳': 1, '合作': 1, '张贴': 1, '冲进': 1, '开至': 1, '南巡': 1, '传给': 1, '刊登': 3, '派出': 7, '超过': 1, '途经': 1, '集结出发一抵达': 1, '提起': 1, '任': 4, '任命': 3, '进入': 6, '诊断': 1, '治疗': 3, '扑灭': 1, '转到': 1, '当选': 1, '选派': 1, '被开除': 5, '滞留': 1, '领取': 1, '同意': 1, '位于': 1, '冒领': 1, '立案审查': 1, '联系': 3, '加快恢复': 1, '部署': 1, '组织或授意': 1, '搭建': 2, '立案审查调查': 2, '设置': 2, '用在': 1, '优化': 1, '组织召开': 1, '爆发': 4, '担任': 5, '打电话': 1, '整理汇总': 1, '主持召开': 2, '起飞离开': 1, '共建': 1, '编写': 1, '编发': 1, '赶赴': 1, '称赞': 4, '致以': 5, '打败': 5, '任职': 1, '打电话给': 1, '进驻': 1, '采访': 2, '合作完成': 1, '写出': 2, '爆出': 1, '发送': 1, '突发': 1, '报告': 2, '默哀': 1, '看到': 2, '调任': 1, '被确诊': 11, '逮捕': 50, '下沉': 1, '赠送': 1, '砍伤': 1, '落户': 1, '出生': 2, '反对': 37, '回击': 1, '提出申诉': 1, '连线': 1, '免去': 1, '恢复至': 1, '修订': 1, '丧失': 1, '发': 1, '批评': 3, '去世': 50, '下降到': 1, '致信': 3, '安全技术性能检测和整修': 1, '实行': 3, '直飞': 1, '暂停': 1, '判决': 2, '案件退回': 1, '参与建议': 2, '批复同意': 1, '连续四天发布': 1, '研制': 1, '有序开展': 1, '上报': 1, '乘坐': 1, '表达': 1, '突增': 1, '鸣着笛通过': 1, '就地转入': 1, '依然执行': 1, '享受': 1, '新发现': 1, '迅速展开': 0, '再次发生': 1, '列出': 1, '抢建': 1, '连续三天发布': 1, '乘': 6, '封城': 1, '发了': 1, '受到': 4, '修建': 1, '制造': 23, '作了': 1, '迁到': 1, '见了': 1, '写了': 3, '肯定': 1, '查阅': 1, '焕然一新': 1, '陪同': 2, '篡改': 3, '带队参加': 1, '定在': 1, '没参加': 1, '写信': 3, '强渡': 1, '下达': 1, '找': 2, '召集': 3, '构成': 1, '打听': 1, '授予': 6, '致函': 2, '领命': 1, '颁布': 7, '回到': 1, '共同主编': 1, '支持创办': 1, '执政': 1, '访问': 3, '歼': 1, '审讯': 1, '住了': 1, '响应': 3, '只接受': 1, '被': 2, '袭击': 38, '创办': 3, '首创': 1, '已有': 1, '等了': 1, '来': 2, '派': 2, '沟通': 1, '考入': 1, '是': 1, '响起': 1, '传达': 1, '开得': 1, '逢迎': 1, '夺走': 1, '主张': 1, '特批': 1, '讲演': 1, '提议': 3, '做过': 1, '拉拢': 1, '插手': 3, '致力': 1, '打破': 1, '调': 0, '历数': 1, '严惩': 1, '改革': 1, '拟定': 1, '汇报': 0, '沟通出席': 1, '不支持': 1, '获得': 23, '判处': 6, '举报': 50, '发射': 1, '未参加': 1, '脱下': 1, '不再接受': 1, '少接受': 1, '被派往': 1, '释放': 1, '通知': 1, '枪击': 12, '告别': 1, '视察': 1, '侵蚀': 1, '患上': 1, '发言': 1, '写下': 1, '打了': 1, '发动': 3, '见面': 2, '亲抓': 1, '进攻': 2, '放了': 1, '缴获': 1, '发报': 1, '率领': 2, '密商': 1, '占领': 2, '发电': 1, '播送': 1, '讲话': 1, '录取': 1, '批判': 1, '批给': 1, '资助': 1, '关押': 1, '拜访': 1, '坚持': 1, '转隶': 1, '补偿': 1, '改善': 2, '指示': 1, '北京': 1, '捕杀': 1, '入侵': 1, '得出': 1, '提倡': 1, '掌握': 1, '观礼': 1, '遵守': 1, '促推': 0, '拨款': 1, '索取': 2, '转载': 2, '增添': 1, '失业': 1, '反击': 2, '狙击': 1, '检获': 1, '流传': 1, '选用': 1, '拦车': 1, '打击': 2, '捣破': 1, '生效': 1, '驱逐': 1, '无视': 1, '防疫': 2, '等候': 1, '包围': 1, '阻止': 1, '上升': 1, '扮演': 1, '谋求': 1, '截获': 1, '拨出': 2, '反映': 1, '炒作': 2, '探望': 1, '贴出': 1, '聚集': 1, '派发': 1, '叫停': 1, '背负': 1, '抗击': 1, '选举': 4, '引发': 1, '产生': 1, '协助': 2, '承认': 1, '回归': 2, '禁止': 4, '干预': 4, '改建': 1, '挑起': 1, '启用': 0, '推翻': 1, '反制': 1, '指责': 1, '面临': 1, '作为': 3, '碰到': 1, '追问': 1, '煽动': 2, '颁发': 1, '吸纳': 1, '限制': 1, '取消': 2, '揭发': 1, '引起': 1, '联络': 1, '宣告': 1, '停职': 19, '停止': 1, '入住': 1, '代表': 1, '讲述': 1, '告诫': 1, '诞下': 4, '列作': 1, '暴露': 1, '分配': 1, '保持': 1, '追踪': 1, '延伸': 1, '抹黑': 1, '制止': 1, '使用': 1, '团结': 1, '涉及': 2, '注重': 1, '破坏': 1, '聚会': 1, '为': 1, '扭曲': 1, '缓刑': 1, '拒绝': 2, '有违': 1, '认同': 1, '放入': 1, '发文': 1, '宣扬': 1, '攻击': 5, '翻查': 1, '担心': 1, '当作': 1, '放有': 1, '开会': 1, '停止发布': 2, '讲解': 1, '订购': 1, '请求': 2, '称': 3, '修改': 1, '递交': 1, '改为': 1, '召见': 1, '注册': 1, '出口': 1, '上涨': 9, '登上': 1, '打掉': 1, '察看': 1, '进': 1, '降低': 4, '重启': 1, '调整为': 2, '检出': 1, '筛查出': 1, '裁员': 50, '裁减': 3, '裁撤': 1, '大裁员': 1, '裁掉': 18, '连裁': 1, '被裁': 1, '坍塌': 33, '塌陷': 2, '侧翻': 10, '倾斜': 1, '垮塌': 12, '倒塌': 9, '塌方': 3, '垮塌事件': 1, '脱落': 1, '溃坝': 1, '解约': 18, '交易': 3, '送出': 5, '解除合约': 1, '合约已经圆满到期': 1, '贱卖': 1, '召回': 50, '收回': 1, '约谈': 50, '约谈会': 1, '约见谈话': 1, '道谢': 4, '感激': 2, '致谢': 4, '感谢信': 6, '感恩': 1, '表谢意': 1, '降息': 15, '下调': 6, '减息': 1, '爆炸': 44, '爆燃': 1, '闪爆': 2, '爆炸事件': 1, '爆鸣': 1, '降价': 10, '官降': 1, '狂降': 0, '直降': 2, '价格下滑': 1, '降到': 1, '跌到': 0, '跌至': 1, '下降': 1, '跌': 2, '降': 1, '下滑': 0, '会面': 4, '会谈': 8, '会晤': 2, '退役': 22, '结束篮球生涯': 1, '生女': 1, '产下': 4, '生下': 9, '生子': 4, '产女': 5, '生儿子': 1, '生的': 1, '早产': 1, '产子': 2, '产下二胎': 1, '荣获': 35, '获奖者': 1, '获奖': 50, '获得“文华大奖”': 1, '荣膺': 1, '获': 3, '获省二等奖': 1, '喜获': 2, '摘得': 2, '颁给': 1, '一等奖': 1, '金曲奖': 2, '获最佳宽窄带融合终端奖': 1, '特等奖': 1, '诺奖得主': 1, '大奖': 6, '拿下': 11, '创新飞跃奖': 1, '得主': 0, '获首届“科学探索奖”': 1, '入围': 1, '斩获': 5, '诺贝尔文学奖': 1, '花落': 1, '奖项': 1, '获诺贝尔和平奖': 1, '获颁谷歌Material Design 年度设计大奖': 0, '展示': 3, '开播': 7, '正式官宣': 0, '发售': 3, '首发': 7, '亮相': 12, 'PS4版定档': 1, '推送': 5, '发布会': 8, '登场': 1, '正式亮相': 2, '最新': 1, '面世': 1, '正式发表': 0, '官宣': 2, '新推': 0, '开启了公测': 1, '上架': 4, '出版': 2, '推行': 1, '推': 1, '登陆': 9, '解锁': 1, '开启预售': 1, '正式开售': 0, '正式上市': 1, '更新': 2, '公开': 2, '正式到来': 1, '开卖': 1, ' 发布': 1, '隆重发布': 1, '登陆PS平台': 1, '新系列': 2, '播出': 3, '出炉': 0, '出品': 1, '正式上线': 3, '点赞': 50, '赞誉': 1, '赞扬': 2, '赞赏': 1, '上映': 50, '定档': 40, '公映': 10, '首映': 6, '放送': 1, '改档': 1, '点映': 1, '登录': 1, '首播': 1, '失联': 22, '走失': 5, '失去联系': 1, '失踪': 14, '下落不明': 1, '探班': 50, '抓获': 50, '抓': 4, '行政拘留': 9, '拘留': 50, '被捕': 6, '拘捕': 15, '刑拘': 18, '刑事拘留': 6, '批捕': 2, '抓回': 1, '落网': 1, '被抓': 7, '押解': 4, '捉拿归案': 1, '追捕': 1, '抓捕': 8, '查获': 1, '押回': 1, '缉捕': 1, '行拘': 4, '自首': 1, '到案': 1, '被拘': 2, '报捕': 1, '擒获': 1, '引渡': 1, '逮捕令': 1, '退出': 50, '离队': 5, '离去': 1, '失去': 1, '退队': 2, '撤出': 1, '欢送': 1, '洪水': 6, '山洪': 8, '洪涝灾害': 1, '洪水灾害': 1, '游行': 22, '游行集会': 1, '加息': 14, '坠毁': 36, '毁致': 1, '失事货机': 1, '坠机': 4, '道歉': 43, '致歉': 13, '致歉信': 1, '歉意': 2, '深表歉意': 1, '开幕': 50, '启幕': 8, '开幕式': 43, '拉开帷幕': 1, '启幕仪式': 1, '开幕仪式': 4, '开营': 2, '拉开序幕': 2, '揭幕': 0, '拉开战幕': 1, '退赛': 26, '离场': 2, '伤退': 5, '退出比赛': 2, '分手': 50, '分开': 1, '情断': 1, '出售': 21, '拍卖': 7, '购入': 0, '拍下': 1, '竞得': 4, '出让': 6, '回购': 3, '卖给': 1, '转让': 6, '净卖出': 0, '放售': 1, '摘': 1, '再购': 1, '卖油': 1, '卖掉': 1, '售卖': 2, '成交': 1, '接手': 1, '售予': 0, '买下': 2, '怀孕': 5, '怀二胎': 1, '涨停': 50, '涨停板': 17, '跌停': 42, '立案': 50, '罚款': 50, '罚没款': 1, '处罚': 4, '判罚': 1, '遭罚': 3, '100万': 1, '罚单': 4, '90万': 1, '重罚': 1, '罚': 6, '罚金': 3, '求婚': 50, '开庭': 50, '公开审理': 4, '再审': 1, '宣判': 3, '公开宣判': 4, '审判': 1, '出庭': 1, '撤下': 0, '删除': 1, '公诉': 31, '诉讼': 7, '提起诉讼': 2, '提起公诉': 4, '指控': 1, '起诉状': 1, '民事诉讼': 1, '告上法庭': 2, '再诉': 1, '起诉书': 1, '诉至': 2, '上诉': 2, '诉': 1, '告上': 1, '告': 1, '离职': 19, '辞任': 33, '辞职': 50, '辞去': 50, '正式卸任': 1, '卸任': 18, '合作停止': 1, '退任': 4, '离任': 3, '卸下': 1, '辞呈': 2, '退休': 1, '辞': 0, '签约': 29, '引进': 6, '加盟': 50, '签下': 34, '复出': 1, '去了': 2, '委任': 1, '送出了': 1, '补招': 2, '换来': 1, '带回': 1, '迎来': 1, '转会': 9, '入队': 1, '合约': 1, '得到': 2, '就任': 1, '跳槽': 2, '投奔': 1, '达成了一份多年的协议': 1, '签署合同': 1, '认领': 1, '转投': 1, '买进': 1, '解散': 17, '空袭': 12, '遭袭': 2, '杀害': 5, '遇袭': 4, '炮击': 2, '来袭': 1, '刀砍': 1, '打': 1, '殴打': 4, '刺向': 1, '枪击事件': 2, '捅伤': 3, '轰炸': 1, '枪击案': 1, '突袭': 2, '围殴': 2, '不明腐蚀液体飞洒而下': 1, '刺伤': 1, '轰击': 1, '持刀刺': 1, '天降腐蚀液体': 1, '死亡': 50, '遇难': 5, '身亡': 50, '逝世': 17, '离世': 12, '过世': 3, '致死': 7, '遇害': 4, '溺亡': 6, '自杀': 6, '牺牲': 9, '打死': 1, '死': 5, '死者': 3, '丧生': 3, '刺死': 2, '离开人世': 2, '仙逝': 1, '自刎': 2, '遗体': 2, '痛失': 1, '咽气': 1, '葬礼': 1, '横死': 1, '毙命': 0, '坠亡': 4, '猝死': 0, '自尽': 0, '辞世': 2, '病故': 1, '生命的陨落': 1, '枪杀': 1, '病逝': 1, '殉职': 1, '没能醒来': 1, '无生命体征': 1, '丧命': 1, '尸体': 2, '走了': 1, '砸死': 0, '过劳死': 1, '订婚': 18, '婚期已定': 1, '婚礼': 50, '离婚': 50, '离了': 1, '离婚声明': 1, '告吹': 1, '禁赛': 50, '禁止参加国足比赛': 1, '停赛': 2, '冠军': 50, '夺得': 5, '夺冠': 49, '金牌': 20, '捧得': 1, '第一名': 3, '金腰带': 1, '金': 5, '卫冕': 3, '夺魁': 1, '联赛冠军': 1, '摘金': 2, '2连冠': 1, '总冠军': 8, '争冠': 2, '夺得三冠': 1, '连冠': 1, '首冠': 2, '桂冠': 3, '夺金': 2, '第9冠': 1, '摘冠': 1, '夺得冠军': 1, '三连冠': 1, '夺4金': 1, '周冠军': 2, '获得冠军': 1, '冠亚军': 1, '第一金': 1, '摘得4金': 1, '勇夺': 2, '7连冠': 1, '获一等奖': 1, '摘首金': 1, '七连冠': 1, '撞到': 4, '交通事故': 38, '撞上': 11, '车祸': 27, '相撞': 14, '撞出': 2, '撞倒': 4, '撞车': 1, '碰撞': 8, '撞飞': 4, '事故': 3, '抢行': 1, '撞伤': 2, '火车事故': 1, '刮蹭': 1, '追尾': 5, '侧翻事故': 2, '撞进': 1, '撞昏': 1, '被撞': 1, '翻车': 3, '脱轨': 1, '坠江': 1, '坠入': 1, '追尾事故': 2, '撞击': 2, '碰撞事故': 1, '撞高架': 1, '撞在一起': 1, '结婚': 50, '领证': 8, '迎娶': 3, '嫁给': 7, '结婚证': 1, '结完婚': 1, '进入礼堂': 1, '成婚': 1, '婚姻': 1, '婚后': 3, '嫁': 3, '大婚': 2, '新婚': 1, '完婚': 2, '结了婚。': 1, '闪婚': 2, '娶到': 1, '下嫁': 1, '婚姻登记': 0, '娶': 2, '晚婚': 1, '起火': 31, '纵火': 6, '着火': 9, '自燃': 7, '火灾': 22, '大火': 9, '山火': 2, '火情': 1, '起火点': 1, '被烧': 1, '失火': 2, '起了火': 1, '发生火情': 1, '罢工': 23, '融资': 50, '获投': 1, '涨价': 7, '涨': 2, '日涨幅': 1, '涨幅': 4, '大涨': 2, '上扬': 1, '飚升': 1, '狂升': 1, '跳涨': 1, '暴涨': 1, '提价': 1, '举报信': 1, '出轨': 8, '婚外情': 1, '生日': 47, '过37岁生日': 1, '庆生': 50, '过生日': 3, '生日会': 3, '生日快乐': 1, '大寿': 1, '庆祝': 1, '寿星': 1, '共庆生日': 2, '贺生': 1, '祝福': 1, '庆祝生日': 3, '贺寿': 1, '庆生照': 1, '公开募股': 1, '输给': 29, '取胜': 13, '赢': 7, '战胜': 50, '击败': 50, '被吊打': 1, '3:0': 2, '输': 36, '击落': 1, '获胜': 8, '大胜': 50, '狂胜': 14, '惨败': 33, '4-0': 8, '不敌': 50, '拿下了比赛': 1, '11:3': 1, '力克': 28, '淘汰': 36, '小胜': 12, '失败': 1, '126-67': 1, '横扫': 50, '0-1': 5, '全胜': 3, '轻取': 19, '险胜': 50, '胜': 45, '完败': 13, '旗开得胜': 2, '逆转': 38, '连胜': 28, '首胜': 8, 'KO': 1, '胜利': 25, '0-3': 1, '负于': 15, '2-0': 4, '客负': 1, '赢得': 2, '赢下': 12, '惜败': 23, '赢了': 3, '小负': 2, '连败': 9, '1-2': 1, '完虐': 1, '再下一城': 1, '败给': 4, '落败': 5, '憾负': 10, '输掉': 11, '吊打': 5, '完胜': 32, '128-118': 1, '打爆': 1, '26-22': 1, '4-1': 4, '3比2': 1, '2：0': 0, '三连胜': 1, '10-5': 1, '0比2': 2, '0：2': 2, '3-2': 4, '胜出': 3, '失利': 8, '14-0': 1, '13-0': 2, '再胜': 2, '首败': 3, '击沉': 1, '超越': 1, '栽在': 1, '输球': 6, '2：1': 1, '赢球': 2, '3比1': 1, '零封': 10, '0：1': 2, '连输': 2, '翻盘': 3, '1-0': 2, '3-1': 4, '1比2': 1, '血洗': 1, '绝杀': 10, '67-60': 1, '2:1': 1, '5-0': 3, '0比1': 1, '负': 15, '2比1': 2, '败': 5, '1比0': 1, '败北': 1, '7-3': 1, '3:1': 1, ' 2-1': 1, '2比4': 1, '3-0': 10, '连克': 1, '干掉': 1, '1-3': 2, '1:0': 2, '5-4': 1, '终结': 2, '4-3': 2, '告负': 2, '力压': 1, '83-95': 1, '2-1': 1, '败仗': 1, '败于': 1, '输了': 1, '1：0': 1, '拿下了这场比赛': 1, '6胜': 1, '双杀': 1, '不胜': 1, '先丢': 1, '67：84': 1, '115-109': 1, '速胜': 1, '4比9': 1, '1：3': 1, '125-89': 1, '赢下了': 1, '4比1': 1, '暴打': 1, '擒': 1, '捍卫主场': 1, '打懵': 1, '开门红': 1, '击溃': 2, '4-2': 1, '0比3': 1, '39-0': 1, '制胜': 1, '大获全胜': 2, '全取三分': 1, '大逆转': 1, '负场': 1, '31-17': 1, '撼负': 1, '大败': 1, '攻克': 1, '2-3': 2, '惨负': 1, '67比59': 1, '0-2': 1, '4比0': 1, '力斩': 1, '有期徒刑': 45, '被判': 3, '获四年刑': 1, '监禁': 3, '判无期': 1, '获刑23年': 2, '被判有期徒刑': 1, '获刑': 23, '获刑14年': 1, '拘役': 5, '判刑': 1, '判处有期徒刑': 1, '入狱': 2, '长期徒刑': 1, '免职': 0, '解雇': 11, '双开': 1, '解除劳动合同': 0, '晋级': 50, '杀进': 1, '进军': 1, '闯进': 2, '挺进': 3, '打入决赛': 1, '决赛': 3, '出线': 3, '过关': 1, '半决赛': 1, '杀入': 1, '杀进了8强': 1, '送入': 1, '闯入': 1, '进入到S9小组赛': 1, '闭幕式': 12, '闭幕': 13, '落幕': 9, '落下帷幕': 1, '跌停板': 11, '地震': 50, '矿震': 2, '答谢': 1, '生孩子': 1, '获香港国际青年电影节最具潜力演员奖': 1, '夺': 1, '连发': 1, '出一机': 1, '正式亮相。': 0, '开售': 1, '大赞': 1, '看望': 1, '游行示威': 1, '坠落': 1, '土拍': 1, '怀上': 1, '司法诉讼': 1, '返回': 1, '亡': 1, '摔死': 1, '轻生': 1, '不治身亡': 1, '被枪杀': 1, '离了婚': 2, '五冠': 1, '三车受损': 1, '严重事故': 1, '翻车事故': 1, '结了婚': 1, '嫁入豪门': 1, '砍翻': 1, '挫败': 1, '先丢一局': 1, '2-4': 1, '取得胜利': 1, '连丢两局': 0, '力退': 0, '攻陷': 1, '77-73': 1, '2:0': 1, '被判五年': 1, '求刑': 1, '封上跌停板': 1, '校长': 50, '配音': 50, '票房': 50, '主题曲': 50, '饰演': 50, '代言人': 50, '爱好': 0, '身份': 0, '价格': 0, '价格单位': 0, '加工': 1, '铁丝': 0, '看': 1, '种': 1}
```

欢迎大家在issue贴出自己在该数据集上的工作  
