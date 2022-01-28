IndexError: invalid index of a 0-dim tensor. Use tensor.item() to convert a 0-dim tensor to a Python

## 报错原因分析:

train_loss += loss.data[0] 是pytorch0.3.1版本代码,在0.4-0.5版本的pytorch会出现警告,不会报错,但是0.5版本以上的pytorch就会报错,总的来说是版本更新问题.

## 解决方法:

## 将原语句：

train_loss+=loss.data[0]

## 修改为：

train_loss+=loss.item()

