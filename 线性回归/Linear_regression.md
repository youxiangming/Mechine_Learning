# 线性回归：
  1.基本要素  
  2.python代码的实现  
  3.pytorch版  
  笔者理解：
  此模型是一个预测的模型。它可以通过提取物体或事件的特征，并且通过训练，可以分辨是否为同一类或预测事件发生的概率。
  训练的过程就是：建立特征与结果的联系，即寻找：权重（w1）和偏置(p);
  		
## 一.基本要素：
  * 线性回归的模型：  
	1. 预测值=w1*特征+b  
		h(x)=w1*x+b
	2. 假设以预测房价为模型，一套房屋则为一个样本  
		样本(example)：    
		  - 特征（feature）：  
			1.房屋的面积（area）  
			2.房屋的时间（data）  
			3.房屋的位置（position）  
			4.房屋的样式（shape）  
			......等特征。  
		  - 标签(label)：房价(price)
	
  * 数据集(data_set)：多个样本的集合。  
	  1. 训练数据集（training data set）  
			 用来训练模型的参数，即 w1,b;
	  2. 测试数据集（training set）  	
			 用来验证模型的准确度。用未参与训练的数据进行测试
	
  * 损失函数（Loss_Function）:

      误差（Loss）：真实值(y)与预测值(y')之间的差值。这里一般用一个非负数来表示
      (凡是模型预测的都会有误差，所以我们用一个变量（Loss）来度量这个误差）：  
      公式为：
      $$
      l^{(i)}(\mathbf{w}, b) = \frac{1}{2} \left(\hat{y}^{(i)} - y^{(i)}\right)^2,
      $$

      $$
      
      L(\mathbf{w}, b) =\frac{1}{n}\sum_{i=1}^n l^{(i)}(\mathbf{w}, b) =\frac{1}{n} \sum_{i=1}^n \frac{1}{2}\left(\mathbf{w}^\top 		\mathbf{x}^{(i)} + b - y^{(i)}\right)^2.
      $$

      

  * 优化函数 - 随机梯度下降（这是一种求解损失最小的一种方法，此外，还有很多种求解最小值得方法）   
	当模型和损失函数形式较为简单时，上面的误差最小化问题的解可以直接用公式表达出来。这类解叫作解析解（analytical solution）（使用类似函数解析式的一种方式来表示）  
	本节使用的线性回归和平方误差刚好属于这个范畴。然而，大多数深度学习模型并没有解析解，只能通过优化算法有限次迭代模型参数  
	可能降低损失函数的值。这类解叫作数值解（numerical solution）。
	在求数值解的优化算法中，小批量随机梯度下降（mini-batch stochastic gradient descent）在深度学习中被广泛使用。  
	它的算法很简单：先选取一组模型参数的初始值，如随机选取；接下来对参数进行多次迭代，使每次迭代都可能降低**损失函数**的值。 
	在每次迭代中，先随机均匀采样一个由固定数目训练数据样本所组成的小批量（mini-batch）$\mathcal{B}$，  
	然后求小批量中数据样本的  [^平均损失有关模型参数的导数（梯度）]，最后用此结果与预先设定的一个正数的积作为模型参数在此次迭代的**减小量**。
	$$
	(\mathbf{w},b) \leftarrow (\mathbf{w},b) - \frac{\eta}{|\mathcal{B}|} \sum_{i \in \mathcal{B}} \partial_{(\mathbf{w},b)} l^{(i)}	(\mathbf{w},b)
	$$
	学习率: $\eta$代表在每次优化中，能够学习的步长的大小[**就是每次迭代权重改变的速率**]    
	批量大小: $\mathcal{B}$是小批量计算中的批量大小batch size   
	总结一下，优化函数的有以下两个步骤：  
	
	- 初始化模型参数，一般来说使用随机初始化；
	- 我们在数据上迭代多次，通过在负梯度方向移动参数来更新每个参数,最终在损失函数最小的时候找到  
	**此模型最好的权重与偏置**
## [python代码的实现](https://github.com/youxiangming/Mechine_Learning/blob/master/%E7%BA%BF%E6%80%A7%E5%9B%9E%E5%BD%92/%E7%BA%BF%E6%80%A7%E5%9B%9E%E5%BD%92python.ipynb)
## [pytorch版](https://github.com/youxiangming/Mechine_Learning/blob/master/%E7%BA%BF%E6%80%A7%E5%9B%9E%E5%BD%92/pytorch%E7%BA%BF%E6%80%A7%E5%9B%9E%E5%BD%92.ipynb)

