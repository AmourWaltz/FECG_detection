## FECG detection：

* 深度学习：一维CNN，LSTM等；步骤：检测QRS波定位心拍，计算心率
* 传统方法：独立成分分析，小波变换，自适应噪声抵消等；步骤：去除工频噪声，分离母体信号，得到纯净的胎儿心电信号

## 框架：心拍分类+滑动窗口检测+NMS定位：

* 制作数据集，在一段完整心电信号上，根据已获取标签前后各截取一定长度的信号片段，该片段长度与采样频率，预测心率等有关，作为正样本，表示该位置有心跳；再从同样的心电信号上截取没有心跳的同样长度的片段作为负样本，与正样本片段之间的重合度应尽可能小。
* 训练集，验证集，测试集约10：1：2划分，并随机排序。
* 训练好框架后，在信号片段上依次滑动，获取预测概率值的序列，再根据非极大抑制结合两次心跳最短间隔等信息定位心拍。
* 一维CNN与LSTM检测常人心电信号均可达到99%以上，一维CNN收敛更快，但模型相对简单。使用常人的心电信号测试，由于QRS波特征明显很容易检测出，符合预期，可用于特征复杂的胎儿信号，根据测试结果适当改进。

## 胎儿心电信号测试：

* 数据集：PhysioNet Computing in Cardiology Challenge 2013 比赛的数据集，共75条来自不同个体的四导联正常胎儿心电图，均为一分钟长的腹导信号，选取其中一条导联信号，可截取一万条正常胎儿心跳片段，制作数据集。
* 原先网络修改后测试结果：一维CNN，四层卷积网络，框架过于简单，正确率仅50%，基本什么特征都没学出来；LSTM 100隐藏单元，正确率60%，无过拟合。
* 双向LSTM 100隐藏单元，正确率仍仅有60%，无过拟合；一维AlexNet及ResNet，正确率均只有50%。
* CNN及其优化的网络貌似不能直接用，学不出想要的特征；LSTM学到了一些特征，可以考虑优化

## 总结：

* 我觉得由于噪声信号太明显，卷积核太小检测到过多噪声特征所以CNN学不出想要的特征，LSTM也只能学到部分特征仍有很大干扰，与网络复杂程度无关。
* 下一步我打算两个方向同时进行，深度学习方法继续找性能更佳的网络，最好能把CNN和LSTM结合；然后使用传统方法去噪，我觉得对网络干扰比较大的还是噪声信号，使用传统方法把去噪后的信号输入神经网络应该可以达到较好的效果。

 [A Multi-step Approach for Non-invasive Fetal ECG Analysis.pdf](../../FECG_2013DB/paper/A Multi-step Approach for Non-invasive Fetal ECG Analysis.pdf)  [A Multi-step Approach for Non-invasive Fetal ECG Analysis.pdf](../../FECG_2013DB/paper/A Multi-step Approach for Non-invasive Fetal ECG Analysis.pdf) 

 [A Novel Noninvasive Technique to Recognize Fetal QRS Complexes from Noninvasive Fetal Electrocardiogram Signals.pdf](../../FECG_2013DB/paper/A Novel Noninvasive Technique to Recognize Fetal QRS Complexes from Noninvasive Fetal Electrocardiogram Signals.pdf) 

 [A Robust Algorithm for Fetal QRS Detection using Non-invasive Maternal Abdomenal ECGs.pdf](../../FECG_2013DB/paper/A Robust Algorithm for Fetal QRS Detection using Non-invasive Maternal Abdomenal ECGs.pdf)  [index.html](../../FECG_2013DB/paper/index.html) 

 [A Novel Noninvasive Technique to Recognize Fetal QRS Complexes from Noninvasive Fetal Electrocardiogram Signals.pdf](../../FECG_2013DB/paper/A Novel Noninvasive Technique to Recognize Fetal QRS Complexes from Noninvasive Fetal Electrocardiogram Signals.pdf)  [index.html](../../FECG_2013DB/paper/index.html) 

 [A Multi-step Approach for Non-invasive Fetal ECG Analysis.pdf](../../FECG_2013DB/paper/A Multi-step Approach for Non-invasive Fetal ECG Analysis.pdf) 