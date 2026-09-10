# 中芯国际（688981）5分钟做T研究

## 项目目标

使用中芯国际5分钟行情构建预测模型，预测未来一段时间的价格方向，
并研究有底仓条件下的日内做T策略。

本项目目前用于量化研究和历史回测，不直接用于实盘交易。

## 交易约束

1. 不允许裸卖空。
2. 当日新买入的股票不能在当日卖出。
3. 卖出数量不得超过 sellable_position。
4. 信号、目标持仓、订单和实际成交必须分开处理。
5. 收到实际成交结果后才能更新持仓。
6. 回测必须计入佣金、税费、滑点及其他必要成本。
7. 具体交易规则和费率在运行前按最新官方及券商口径核验。

## 核心持仓变量

- total_position：账户当前总持仓
- sellable_position：当日允许卖出的持仓
- today_bought：当日新买入、当日不可卖出的持仓

基本关系：

total_position = sellable_position + today_bought

## 研究流程

原始数据
→ 数据清洗
→ 特征工程
→ 模型训练
→ 信号生成
→ 目标持仓
→ 订单
→ 成交
→ 持仓和资金更新
→ 成本计算
→ 回测评价

## 项目结构

- config：参数配置
- data/raw：原始数据
- data/processed：清洗后的数据
- notebooks：探索性分析
- src/data：数据读取和清洗
- src/features：特征计算
- src/models：模型训练与预测
- src/backtest：回测、持仓和盈亏
- src/execution：订单与成交
- src/utils：公共工具
- results：图表和结果
- tests：自动化检查

## 当前环境

- macOS 15.3
- Apple Silicon arm64
- Python 3.13.7
- VeighNa 4.4.0