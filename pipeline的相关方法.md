### 数据补全方法sklearn.impute.SimpleImputer
```
class sklearn.impute.SimpleImputer(*, missing_values=nan, strategy='mean', fill_value=None, verbose=0, copy=True, add_indicator=False)
```
```
missing_value: 缺失值，空值，也就是np.nan
strategy: 填补空值的策略，一般包括四种方法，mean,median适用于数值类型字段，most_frequent众数，constant自定义，需要配合fill_value使用
copy:则表示对原来没有填充的数据的拷贝
add_indicator:如果该参数为True，则会在数据后面加入n列由0和1构成的同样大小的数据，0表示所在位置非空，1表示所在位置为空。相当于一种判断是否为空的索引
```

### pipeline

可以将特征提取，归一化，分类组织组合在一起，形成一个机器学习工作流，也可以将多个算法模型串联起来
1. 直接调用fit和predict方法对pipeline的所有方法进行训练和预测
2. 可以结合grid search方法对参数进行选择

```
cat_pipeline = Pipeline([
        ("select_cat", DataFrameSelector(["Pclass", "Sex", "Embarked"])),
        ("imputer", MostFrequentImputer()),
        ("cat_encoder", OneHotEncoder(sparse=False)),
    ])
```
