## FECG提取步骤：

* 工频噪声过滤，母胎信号分离，得到纯净的胎儿心电信号

## 传统方法：

* 自适应噪声抵消（ANC）：初步MATLAB实现，相对简单，需要先验知识（工频噪声信号，其他噪声源）较多，工频去噪一步较难实现，母胎信号分离的非线性系统表现不好，因此效果不明显
* 独立成分分析（ICA）：大致了解步骤，对数学要求较高，虽然对所有步骤都适用，但短期内感觉难以优化，只做辅助方法考虑
* 小波变换：同上

## 深度学习方法：

* 所有步骤都适用，可以单独每步分别搭框架，也可以直接端对端输出
* 初步分别用一维CNN和LSTM直接处理，主要为搭建整体框架，效果不要求，能正常处理常人心电信号得出心率即可（获取QRS波，应该较容易处理），尽量于2019年结束前完成
* 接下来使用一些相对高级的框架，适合处理时间序列，尤其是音频信号处理有较好效果，目前查资料可考虑的框架有：WaveNet：扩大感受野；TCN：仿ResNet跳层连接；CLDNN；以及学姐说的Attention网络；
* 根据处理效果自行优化，以及根据实际情况适当引入传统方法

## 数据集：

* MIT-BIH前期处理
* FECGSYNDB：模拟合成信号，适合每一步处理效果及检验

## 时间截点：

* 12月31日前，分别搭好一维CNN和LSTM框架，并对常人心电进行测试，要求均能准确计算常人的心率，数据集采用MIT-BIH数据库心电信号
* 1月17日前：利用之前的网络框架和FECGSYNDB数据集进行胎儿信号的测试，效果不一定理想，然后根据实际情况优化网络结构以及引入传统方法，结合朱老师的数据确定改进方向

## PS：第一篇论文，追求质量，不求速度，，，希望能做得更好更完整一些，不急着短时间发出去，望学姐和朱老师理解！！！