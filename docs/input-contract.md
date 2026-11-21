# 原始资料约定

sources.parquet 是来源贡献行，contribution_id 唯一；相同 order 可含多行。各行 amount/co2 为该供应商的独立贡献，不是重复订单总额。
permissions.jsonl：rule,revision,organization,purpose,start,end,suppliers,categories,columns,grain,effect。* 才表示全选，空列表无授权。grain 是 category-month/order/row；允许更细粒度可用于更粗粒度，但不能反向。deny 按相交范围优先。privacy.json 的 forbidden_joint_slices 直接限定不可共同使用的标签组合，不需要自行推断统计攻击。
release_requests.jsonl 为新请求；receipts.jsonl 为外部签收/取消输入。withdrawals.jsonl 仅撤回指向的 rule/revision，非供应商所有规则。retention.jsonl 是密封保留依据。金额和co2无默认补零。
贡献链接是采购事实关系，不授予权限。签收之外的构建和领取操作由使用者发起，资料中没有预制共享包。

所有名称与数值均为本地合成数据，不代表真实企业、监管结论或生态调查。data/catalog.json 保存文件哈希、原始行数与列；data/updates/ 为后到修订资料，可独立接收。JSON null 表示尚无该值，不与数值零等同；CSV保留原字符串，金额和数量应按十进制解释。来源身份相同且内容相同的重送不产生新业务事实，同身份版本不同内容需保留争议，除明确替代关系外不按到达顺序判定权威。
