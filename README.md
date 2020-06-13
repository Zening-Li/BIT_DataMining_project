# BIT Data Mining 2020

北京理工大学2020年数据挖掘课程项目

### 选题名称：二手车交易价格预测（阿里天池比赛）

#### 比赛数据集

* 训练数据：data/used_car_train_20200313.csv
* 测试数据：data/used_car_testB_20200421.csv
* 提交数据：data/used_car_sample_submit.csv

#### 数据分析及预处理

* 代码：data_process.ipynb
* 预处理后数据： process_data/train_data_v1.csv，process_data/test_data_v2.csv

#### 数据分析内容

* 通过describe()来熟悉训练数据、测试数据数值属性的相关统计量，包括均值，方差，最小值，第1四分位数，中位数，第3四分位数，最大值。
* 通过info()来熟悉数据类型
* 通过可视化方法分析了训练数据、测试数据中的数值属性趋势
* 分析训练数据、测试数据类别特征nunique分布
* 分析训练数据、测试数据缺失值情况
* 对预测属性‘price’ 进行了相关性分析

#### 数据预处理

* ‘price’为长尾分布，对该特征进行了处理，更加符合高斯分布
* SaleID为交易ID，肯定没用，但是我们可以用来统计别的特征的group数量
* name为汽车交易名称，已经脱敏一般没什么好挖掘的，不过同名的好像不少，统计了一下同名数据个数，为name_count，然后删除了属性信息‘name’
* 'seller'、'offerType'特征严重倾斜，训练数据中'seller'有一个特殊值，删除了该样本，而且把‘seller’和‘offerType’属性删除了
* 在题目中规定了power范围为[0, 600]，对数据集中power属性进行了修正
* 'notRepairedDamage'属性中'-'应该也是空值，用nan替换
* 对于缺失值，用众数对缺失值进行了填充
* 对于时间属性信息，‘regDates’和‘creatDates’，增添了6列属性，分别为‘regDate_year’、‘regDate_month’、‘regDate_day’、‘creatDate_year’、‘creatDate_month’、‘creatDate_day’