* 画K线图

  * candlestick_ochl(axes, day, width=0.2, colorup='r', colordown='g')

* numpy优势：

  * 速度：运算速度
  * 在哪里：
    * 内存分布连续
    * 实现并行化运算

* ndarray:

  * 相同类型数据集合
  * N 维数组：
    * 0维：5,   6 
    * 1维：[ 1,2,3,4,5]
    * 2维：[[1,2,3], [3,4,5] ]
    * 3维：[    [[1,2,3], [3,4,5] ], [[1,2,3], [3,4,5] ]       ]
  * 基本属性：
    * 维度：
    * 形状

* 基本操作

  * 创建数组
    * 创建0， 1
    * 从现有的创建：array, asarray, copy
    * 创建固定范围的：np.linspace, np.arange
    * 创建随机值的数组：
      * 正态分布：
        * 平均值
        * 标准差：根号（方差）
        * 方差：反应数据的离散程度

* 股票数据的操作：

  * 索引：通过下标获取

  * 形状：从行：500， 列504 ---> 行：504， 列：500reshape:没有修改原来的形状, 元素数量匹配  resize：修改原来的数组形状stock_day_rise.resize([504, 500])

  * 修改类型：把涨跌幅数据转换成int类型

    stock_day_rise.astype(np.int32)

  * 数据的转换：

    * T 转置
    * tostring() 序列化bytes
    * copy

  * 逻辑运算：

    * 逻辑符号：涨跌幅  > 0.5temp > 0.5

    * 通用判断函数：通用函数判断对所有的数据进行判断返回TRUE，FALSEnp.all(temp > 0.5)

      unique

      np.unique(temp.astype(np.int))

    * 复合逻辑：需求：对于大于> 0.5  小于1 ,1, 0

      复合逻辑运算np.where(temp > 0.5, 1, 0)根据np.logical_and和np.logical_or使用

      np.where(np.logical_and(temp > 0.5, temp < 1), 1, 0)

    * 统计运算：

      * np.mean
      * np.std
      * np.max
      * np.min
      * mp.var

      如果需要统计出哪一只股票在某个交易日的涨幅最大或者最小？

      - np.argmax(temp, axis=)
      - np.argmin(temp, axis=)

    * 数组间运算

      * 广播机制：**Broadcast机制的功能是为了方便不同形状的array（numpy库的核心数据结构）进行数学运算*

        * **相应维度形状一样，或者某个数组位置为1**

      * 数组跟数：

      * 数组跟数组： 用的很少

      * **对比：数组跟数组运算，不管形状怎么改，运算机制已经决定结果**

        **矩阵：满足了我们特定的运算需求**

      * **矩阵运算： 机器学习算法当中会经常用到的一种规则**

        **就是一种特殊的二维数组（运算机制）**

        **array matrix**

        **np. mat是会默认将传入的数组转换成2维矩阵**

        * **运算公式： 必须牢记**

          **(M行，N列) * （N行， L列） = （M行， L列）**  np.matmul

      * 数组的合并和分割

        * 合并这20个股票的数据

        axis=1时候，按照数组的列方向拼接在一起 hstack

        axis=0时候，按照数组的行方向拼接在一起  vstack

        all_ = np.concatenate([stock1, stock2], axis=0) # [20, 200]

        * 分割：split

      * IO操作和数据处理：

        *  np.genfromtxt("./data/numpy_test/test.csv", delimiter=',')
        * np.nan类型： float

    ​

    ​