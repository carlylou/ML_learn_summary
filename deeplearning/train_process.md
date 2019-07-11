## 构建网络



### 第一步：数据预处理
对于图像来说，就是 zero centered. 
1. subtract mean image = [32, 32, 3] array
2. subtract mean channel value 3 numbers for each channel
3. subtract 128.0 then divided by 128.0

### 第二步：构建网络
1. 选择模型
2. 计算Loss
3. 选择optimizer，推荐Adam，lr=1e-3/5e-4; beta1=0.9;beta2=0.999.
4. 计算accuracy
5. summary, 以epoch为单位进行。loss hist. eval+ train accuracy ； 每一层的激活数据及梯度分布。
6. saver 
7. session
8. 初始化变量
9. restore variable
10. train + evel



### 第三步：训练
1. 选择很少一部分数据，进行多个epochs尝试过拟合。
2. 调整学习速率，以对数空间调整。先进行大范围的锁定，少epochs比较，再进行小范围搜索，多epochs比较。
3. 可以对比 引入 或不引入 正则化项 是否会达到更好的效果 （dropout, batchnorm, data augmentation)
4. 对于最优值在边界要小心


### 第四步：模型评价
1. 可以使用同一个训练过程中，不同表现良好的checkpoints来平均表现
2. 同一个模型，同一组超参数，不同初始化。