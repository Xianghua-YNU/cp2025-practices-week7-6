# 实验报告 - Pandas 数据操作练习

## 一、实验目的
阐述本次实验的主要目的，可参考任务目的部分。
答：1.熟悉 Pandas 的数据结构（DataFrame）。
    2.掌握数据的读取和写入操作。
    3.学会数据清洗，包括处理缺失值、异常值。
    4.能够进行数据的基本统计分析和复杂的数据转换。
    5.了解如何使用 Pandas 进行数据可视化。

## 二、实验步骤
详细描述你完成每个任务的步骤和方法，可结合代码进行说明。

### 任务 1: 读取数据
说明你使用的读取数据的函数和过程。
代码：
def load_data():
    """任务1: 读取数据文件"""
    return pd.read_csv('data.csv')
说明：
使用pandas库的read_csv函数读取名为'data.csv'的文件，并将数据以DataFrame形式返回
### 任务 2: 查看数据基本信息
描述如何查看数据的基本信息。
代码：
def show_basic_info(data):
    """任务2: 显示数据基本信息"""
    print("数据基本信息：")
    data.info()
说明：
 调用DataFrame的info方法，打印数据的基本信息，如每列的数据类型、非空值数量等
### 任务 3: 处理缺失值
说明你找出缺失值列和填充缺失值的方法。
代码+注释说明：
def handle_missing_values(data):
    """任务3: 处理缺失值"""
    # 找出数据中存在缺失值的列，将列名转换为列表形式
    missing_columns = data.columns[data.isnull().any()].tolist()
    for col in missing_columns:
        # 判断列的数据类型是否为数值类型
        if pd.api.types.is_numeric_dtype(data[col]):
            # 如果是数值类型，使用该列的均值填充缺失值
            data[col] = data[col].fillna(data[col].mean())
    return data
### 任务 4: 数据统计分析
说明你计算数值列均值、中位数和标准差的方法。
代码+注释说明：
def analyze_statistics(data):
    """任务4: 统计分析数值列"""
    # 选取数据中数据类型为数值类型的列，获取列名
    numeric_columns = data.select_dtypes(include=['number']).columns
    for col in numeric_columns:
        # 计算每列的均值
        mean_value = data[col].mean()
        # 计算每列的中位数
        median_value = data[col].median()
        # 计算每列的标准差
        std_value = data[col].std()
        print(f"{col} 列的均值: {mean_value}, 中位数: {median_value}, 标准差: {std_value}")


### 任务 5: 数据可视化
描述你选择的数值列和绘制直方图的过程。
代码+注释说明：
def visualize_data(data, column_name='成绩'):
    """任务5: 数据可视化"""
    # 对指定列（默认为'成绩'列）绘制直方图
    data[column_name].plot.hist()
    # 显示绘制的图形
    plt.show()

### 任务 6: 数据保存
说明你保存处理后数据的方法。
代码+注释说明：
def save_processed_data(data):
    """任务6: 保存处理后的数据"""
    # 将处理后的数据保存为'processed_data.csv'文件，不保存行索引
    data.to_csv('processed_data.csv', index=False)

## 三、实验结果
展示每个任务的结果，可使用表格或图表进行呈现。

### 任务 1: 读取数据
展示读取的数据的基本信息（如列名、行数等）。
答：
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 5 entries, 0 to 4
Data columns (total 4 columns):
### 任务 2: 查看数据基本信息
粘贴数据的基本信息输出。
<img width="227" alt="image" src="https://github.com/user-attachments/assets/3161b9ef-ff49-4de0-8e3d-1d8159f0243e" />
### 任务 3: 处理缺失值
说明处理后缺失值的情况。
![614a1fbafc902d914551f3d0a4f815f4](https://github.com/user-attachments/assets/594ebe7f-eed3-4526-8a16-b90af3270e53)
### 任务 4: 数据统计分析
列出数值列的均值、中位数和标准差。
答：
年龄 列的均值: 26.25, 中位数: 26.25, 标准差: 3.031088913245535
成绩 列的均值: 86.8, 中位数: 88.0, 标准差: 5.227332015474051

### 任务 5: 数据可视化
插入绘制的直方图。
<img width="455" alt="image" src="https://github.com/user-attachments/assets/742d60ab-e8de-4883-bdd8-fab3cb6eb70c" />
### 任务 6: 数据保存
说明保存的文件路径和文件名。
答：
文件路径：C:\Users\Lenovo\.spyder-py3\processed_data.csv
文件名： processed_data.csv


## 四、总结
总结本次实验的收获和体会，分析遇到的问题及解决方法，对 Pandas 数据操作的理解和认识。
答：
（1）实验收获与体会
 了解并学会了以下几个数据处理的步骤：
1. 数据读取与清洗：学会用 read_csv 读取数据， dropna 等处理缺失、重复值，明白数据预处理的重要性。
2. 数据选择与过滤：掌握 loc 、 iloc 及布尔索引，能灵活提取数据子集。
3. 数据合并与重塑：用 merge 、 concat 拼接数据， pivot 、 melt 完成透视与逆透视，丰富处理复杂数据手段。
（2）问题及解决
1. 大数据集读取慢：设 chunksize 分块读取，减少内存占用，提高效率。
2. 合并失败：因列名不一致，重命名列名解决。
（3）对Pandas理解
Pandas是强大的数据处理工具，简化复杂操作，是数据分析基石，为高级应用提供数据预处理基础，提升处理和分析效率。
    
