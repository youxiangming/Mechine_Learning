线性回归：
  1.基本要素
  2.python代码的实现
  3.pytorch版
  笔者理解：
  此模型是一个预测的模型。它可以通过提取物体或事件的特征，并且通过训练，可以分辨是否为同一类或预测事件发生的概率。
  训练的过程就是：建立特征与结果的联系，即寻找：权重（w1）和偏置(p);
  		
一.基本要素：
  A.线性回归的模型：
  	预测值=w1*特征+b
		h(x)=w1*x+b
	假设以预测房价为模型
	一套房屋则为一个样本
	样本(example)：
		特征（feature）：
			1.房屋的面积（area）
			2.房屋的时间（data）
			3.房屋的位置（position）
			4.房屋的样式（shape）
			......等特征。
		标签(lable)：房价(price)
  B.数据集(data_set)： 多个样本的集合。
  	1.训练数据集（training data set）
		 用来训练模型的参数，即 w1,b;
        2.测试数据集（training set）	
		 用来验证模型的准确度。用未参与训练的数据进行测试
  C.损失函数（Loss_Function）:
  	 误差（Loss）：真实值(y)与预测值(y')之间的差值。这里一般用一个非负数来表示
  	(凡是模型预测的都会有误差，所以我们用一个变量（Loss）来度量这个误差）
	计算公式：
	loss=0.5*(y-y')**2
	
$$
\mathrm{price} = w_{\mathrm{area}} \cdot \mathrm{area} + w_{\mathrm{age}} \cdot \mathrm{age} + b
$$
	