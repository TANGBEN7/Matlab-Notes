# Matlab使用笔记

标签（空格分隔）： PX4源码解读

---
# 基本操作
## 运行
> Note:
如果Matlab一直显示正忙，要`关闭防火墙`

## 命令行界面基本操作
### 变量：
```
>> x = [1 2 3 4 5]; //定义向量，含5个元素(比如散点横坐标)
>> x = [1 2 3 4 5] //定义向量，含5个元素，同时输出x
>> x //输出x
```
> Notes：
> 定义变量后，该变量会出现在右侧工作台

### 图像
- 绘制散点图
```
scatter(x,y); //x，y为等长的向量，对应横纵坐标
```
- polt函数
```
polt(x,y) //做出的是折线图
```
- 绘制光滑曲线

方法一：最小二乘法拟合
```
c = polyfit(x, y, 2);  %进行拟合，c为2次拟合后的系数
d = polyval(c, x, 1);  %拟合后，每一个横坐标对应的值即为d
plot(a, d, 'r');       %拟合后的曲线
```
方法二：插值法
```
x = [...]; //最小值为0，最大值为30
y = [...];
xi = 0:0.001:30; //参数为：最小值：分割密度：最大值
pp = interp1(x,y,xi,'pchip');
plot(xi,pp);
```
- 拟合效果：

![](img/capture_01.jpg)


方法三：Linspace
```
x=[1 2 3 4 5 6];
y=[3 6 8 13 31 24];
xx=linspace(1,6);  %参数：数组x首元素；末元素
yy=spline(x,y,xx);
plot(xx,yy,'r',x,y,'o')  %参数'r'：颜色
```

# 最小二乘法拟合
## 直线拟合
- 计算斜率与截距
```
>> x = [...]; //最小值为0，最大值为30
>> y = [...];
>> k = poltfit(x, y, 1);
>> k  //输出k，第一个参数为斜率，第二个为截距
```
- 作图
```
>> y_min = polyval(0, k);  //计算拟合函数在x=0处取值
>> y_max = polyval(30, k); //计算拟合函数在x=30处取值
>> plot([0,30], [y_min, y_max]); //两点确定直线
```

# Matlab script
Comming soon...
> I will keep updating...

# 其他
## grid函数
- 功能：坐标纸
- 开启坐标纸
```
grid on;
```
- 调整坐标纸density
```
set(gca, 'XMinorGrid','on');
set(gca, 'YMinorGrid','on');
```


