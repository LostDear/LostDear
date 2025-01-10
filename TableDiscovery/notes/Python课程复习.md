**关键字**：逻辑运算and/or/not；定义class/global/def/lambda/import/from；流程if/elif/while/for/else/break/continue/pass/return/yield/with/as；
异常处理try/except/finally/raise/assert；判断is/in；其他del/print/exec
**浮点精度**：取值-1e308~1e308,精度1e-16(sys.float_info)
## 函数

### 数字类型相关函数

- `pow(x,y)`：计算x的y次幂，可以计算非常大的数值，如`pow(2,pow(2,15))`会得到一个非常大的整数。
    
- `round(x, d)`：对浮点数x进行四舍五入，d表示小数截取位数，用于辅助浮点数间的运算及比较，解决浮点数运算中不确定尾数的问题。
### math库相关函数

- math库提供了4个数学常数。
- 数值表示函数：共16个。
- 幂对数函数：共8个。
- 三角双曲函数：共6个。
- 高等特殊函数：共4个。
### 

### 字符串相关函数

- `format()`：字符串的格式化方法，基本使用格式为`<模板字符串>.format(<逗号分隔的参数>)`，用于对字符串进行格式表达。
### time库相关函数

- 时间获取函数：
    
    - `time()`：获取当前时间戳，即计算机内部时间值，返回一个浮点数，如`time.time()`可能返回1516939876.6022282。
        
    - `ctime()`：获取当前时间并以易读方式表示，返回一个字符串，如`time.ctime()`可能返回'Fri Jan 26 12:11:16 2018'。
        
    - `gmtime()`：获取当前时间，表示为计算机可处理的时间格式，返回一个`time.struct_time`对象，如`time.gmtime()`可能返回`time.struct_time(tm_year=2018, tm_mon=1,tm_mday=26, tm_hour=4, tm_min=11, tm_sec=16,tm_wday=4, tm_yday=26, tm_isdst=0)`。
- 时间格式化函数：
    
    - `strftime(tpl, ts)`：将时间格式化为字符串，tpl是格式化模板字符串，ts是计算机内部时间类型变量，如`t = time.gmtime()`后，`time.strftime("%Y-%m-%d %H:%M:%S",t)`会返回'2018-01-26 12:55:20'。
    - `strptime(str, tpl)`：将字符串解析为时间，str是字符串形式的时间值，tpl是格式化模板字符串，如`timeStr = '2018-01-26 12:55:20'`后，`time.strptime(timeStr, "%Y-%m-%d %H:%M:%S")`会返回一个`time.struct_time`对象。
- 程序计时函数：
    - `perf_counter()`：返回一个CPU级别的精确时间计数值，单位为秒，由于计数值起点不确定，通常用于测量两个时间点之间的差值以获取时间间隔，如连续调用`start = time.perf_counter()`和`end = time.perf_counter()`后，`end - start`可得到两者之间的时间差。
    - `sleep(s)`：使程序休眠s秒，s可以是浮点数，如`time.sleep(3.3)`会使程序等待3.3秒后再继续执行。

## matplot
```python
import numpy as np  
from matplotlib import pyplot as plt  
  
# matplotlib的常用函数  
# 1. plt.plot(x, y, format_string, **kwargs) 画图  
#    x: x轴数据  
#    y: y轴数据  
#    format_string: 格式字符串，如'ro'表示红色圆点  
#    **kwargs: 其他参数，如label, linewidth等  
  
# 2. plt.show() 显示图  
#    无参数  
  
# 3. plt.title(label, **kwargs) 图标题  
#    label: 标题文本  
#    **kwargs: 其他参数，如fontsize, color等  
  
# 4. plt.xlabel(xlabel, **kwargs) x轴标签  
#    xlabel: x轴标签文本  
#    **kwargs: 其他参数，如fontsize, color等  
  
# 5. plt.ylabel(ylabel, **kwargs) y轴标签  
#    ylabel: y轴标签文本  
#    **kwargs: 其他参数，如fontsize, color等  
  
# 6. plt.xlim(left, right) x轴范围  
#    left: x轴左边界  
#    right: x轴右边界  
  
# 7. plt.ylim(bottom, top) y轴范围  
#    bottom: y轴下边界  
#    top: y轴上边界  
  
# 8. plt.xticks(ticks, labels, **kwargs) x轴刻度  
#    ticks: 刻度位置  
#    labels: 刻度标签  
#    **kwargs: 其他参数，如rotation, fontsize等  
  
# 9. plt.yticks(ticks, labels, **kwargs) y轴刻度  
#    ticks: 刻度位置  
#    labels: 刻度标签  
#    **kwargs: 其他参数，如rotation, fontsize等  
  
# 10. plt.legend(**kwargs) 图例  
#     **kwargs: 其他参数，如loc, fontsize等  
  
# 11. plt.grid(**kwargs) 显示网格  
#     **kwargs: 其他参数，如color, linestyle等  
  
# 12. plt.savefig(fname, **kwargs) 保存图片  
#     fname: 文件名  
#     **kwargs: 其他参数，如dpi, format等  
  
# 13. plt.figure(**kwargs) 图框  
#     **kwargs: 其他参数，如figsize, dpi等  
  
# 14. plt.subplot(nrows, ncols, index, **kwargs) 子图  
#     nrows: 行数  
#     ncols: 列数  
#     index: 子图索引  
#     **kwargs: 其他参数，如projection等  
  
# 15. plt.subplots(nrows, ncols, **kwargs) 子图  
#     nrows: 行数  
#     ncols: 列数  
#     **kwargs: 其他参数，如figsize, sharex等  
  
# 16. plt.bar(x, height, **kwargs) 条形图  
#     x: x轴数据  
#     height: 条形高度  
#     **kwargs: 其他参数，如width, color等  
  
# 17. plt.scatter(x, y, **kwargs) 散点图  
#     x: x轴数据  
#     y: y轴数据  
#     **kwargs: 其他参数，如color, marker等  
  
# 18. plt.pie(x, **kwargs) 饼图  
#     x: 数据  
#     **kwargs: 其他参数，如labels, autopct等  
  
# 19. plt.hist(x, **kwargs) 直方图  
#     x: 数据  
#     **kwargs: 其他参数，如bins, density等  
  
# 20. plt.plot_date(x, y, **kwargs) 日期格式  
#     x: 日期数据  
#     y: y轴数据  
#     **kwargs: 其他参数，如fmt, tz等  
  
# 21. plt.polar(theta, r, **kwargs) 极坐标  
#     theta: 角度数据  
#     r: 半径数据  
#     **kwargs: 其他参数，如color, linestyle等  
  
# 22. plt.contour(X, Y, Z, **kwargs) 等高线  
#     X: x轴数据  
#     Y: y轴数据  
#     Z: z轴数据  
#     **kwargs: 其他参数，如levels, colors等  
  
# 23. plt.imshow(X, **kwargs) 显示图片  
#     X: 图像数据  
#     **kwargs: 其他参数，如cmap, interpolation等  
  
# 24. plt.text(x, y, s, **kwargs) 添加文本  
#     x: x轴位置  
#     y: y轴位置  
#     s: 文本内容  
#     **kwargs: 其他参数，如fontsize, color等  
  
# 25. plt.annotate(s, xy, **kwargs) 添加注释  
#     s: 注释文本  
#     xy: 注释位置  
#     **kwargs: 其他参数，如xytext, arrowprops等  
  
# 26. plt.style.use(style) 使用样式  
#     style: 样式名称  
  
# 27. plt.close(fig) 关闭图  
#     fig: 图对象  
  
# 28. plt.clf() 清空图  
#     无参数  
  
# 29. plt.cla() 清空坐标轴  
#     无参数  
  
# 30. plt.subplot2grid(shape, loc, **kwargs) 自定义子图  
#     shape: 网格形状  
#     loc: 子图位置  
#     **kwargs: 其他参数，如colspan, rowspan等  
  
# 31. plt.tight_layout(**kwargs) 自动调整子图  
#     **kwargs: 其他参数，如pad, w_pad等  
  
# 32. plt.subplots_adjust(**kwargs) 调整子图  
#     **kwargs: 其他参数，如left, right等  
  
# 33. plt.sca(ax) 设置当前子图  
#     ax: 子图对象  
  
# 34. plt.gca() 获取当前子图  
#     无参数  
  
# 35. plt.gcf() 获取当前图  
#     无参数  
  
# 36. plt.get_cmap(name) 获取颜色映射  
#     name: 颜色映射名称  
  
# 37. plt.colors() 颜色  
#     无参数  
  
# 38. plt.cm() 颜色映射  
#     无参数  
  
# 39. plt.colorbar(**kwargs) 颜色条  
#     **kwargs: 其他参数，如orientation, fraction等  
  
# 40. plt.clabel(CS, **kwargs) 添加等高线标签  
#     CS: 等高线对象  
#     **kwargs: 其他参数，如fontsize, inline等  
  
# 41. plt.contourf(X, Y, Z, **kwargs) 填充等高线  
#     X: x轴数据  
#     Y: y轴数据  
#     Z: z轴数据  
#     **kwargs: 其他参数，如levels, cmap等  
  
# 42. plt.fill(x, y, **kwargs) 填充  
#     x: x轴数据  
#     y: y轴数据  
#     **kwargs: 其他参数，如color, alpha等  
  
# 43. plt.fill_between(x, y1, y2, **kwargs) 填充两个函数之间  
#     x: x轴数据  
#     y1: 第一个函数的y轴数据  
#     y2: 第二个函数的y轴数据  
#     **kwargs: 其他参数，如color, alpha等  
  
# 44. plt.fill_betweenx(y, x1, x2, **kwargs) 填充两个y值之间  
#     y: y轴数据  
#     x1: 第一个函数的x轴数据  
#     x2: 第二个函数的x轴数据  
#     **kwargs: 其他参数，如color, alpha等  
  
# 45. plt.plotfile(fname, **kwargs) 读取文件画图  
#     fname: 文件名  
#     **kwargs: 其他参数，如delimiter, cols等  
  
# 46. plt.streamplot(X, Y, U, V, **kwargs) 流线图  
#     X: x轴数据  
#     Y: y轴数据  
#     U: x方向速度  
#     V: y方向速度  
#     **kwargs: 其他参数，如color, linewidth等  
  
# 47. plt.stem(x, y, **kwargs) 柴火图  
#     x: x轴数据  
#     y: y轴数据  
#     **kwargs: 其他参数，如linefmt, markerfmt等  
  
# 48. plt.step(x, y, **kwargs) 阶梯图  
#     x: x轴数据  
#     y: y轴数据  
#     **kwargs: 其他参数，如where, color等  
  
# 49. plt.boxplot(x, **kwargs) 箱线图  
#     x: 数据  
#     **kwargs: 其他参数，如notch, vert等  
  
# 50. plt.errorbar(x, y, **kwargs) 误差线  
#     x: x轴数据  
#     y: y轴数据  
#     **kwargs: 其他参数，如yerr, xerr等  
  
# 51. plt.eventplot(positions, **kwargs) 事件图  
#     positions: 事件位置  
#     **kwargs: 其他参数，如orientation, colors等  
  
# 52. plt.hexbin(x, y, **kwargs) 六边形箱图  
#     x: x轴数据  
#     y: y轴数据  
#     **kwargs: 其他参数，如gridsize, cmap等  
  
# 53. plt.violinplot(dataset, **kwargs) 小提琴图  
#     dataset: 数据集  
#     **kwargs: 其他参数，如vert, widths等  
  
# 54. plt.table(cellText, **kwargs) 表格  
#     cellText: 单元格文本  
#     **kwargs: 其他参数，如cellColours, colLabels等  
  
# 55. plt.triplot(x, y, triangles, **kwargs) 三角图  
#     x: x轴数据  
#     y: y轴数据  
#     triangles: 三角形顶点索引  
#     **kwargs: 其他参数，如color, linestyle等  
  
# 56. plt.barbs(x, y, u, v, **kwargs) 风羽图  
#     x: x轴数据  
#     y: y轴数据  
#     u: x方向速度  
#     v: y方向速度  
#     **kwargs: 其他参数，如length, pivot等  
  
# 57. plt.quiver(X, Y, U, V, **kwargs) 箭头图  
#     X: x轴数据  
#     Y: y轴数据  
#     U: x方向速度  
#     V: y方向速度  
#     **kwargs: 其他参数，如color, scale等  
  
# 58. plt.stackplot(x, *args, **kwargs) 堆叠图  
#     x: x轴数据  
#     *args: y轴数据  
#     **kwargs: 其他参数，如labels, colors等  
  
# 59. plt.psd(x, **kwargs) 功率谱密度  
#     x: 数据  
#     **kwargs: 其他参数，如NFFT, Fs等  
  
# 60. plt.specgram(x, **kwargs) 谱图  
#     x: 数据  
#     **kwargs: 其他参数，如NFFT, Fs等  
  
# 61. plt.cohere(x, y, **kwargs) 相干性  
#     x: x轴数据  
#     y: y轴数据  
#     **kwargs: 其他参数，如NFFT, Fs等  
  
# 62. plt.xcorr(x, y, **kwargs) 互相关  
#     x: x轴数据  
#     y: y轴数据  
#     **kwargs: 其他参数，如maxlags, normed等  
  
# 63. plt.magnitude_spectrum(x, **kwargs) 幅度谱  
#     x: 数据  
#     **kwargs: 其他参数，如Fs, scale等  
  
# 64. plt.angle_spectrum(x, **kwargs) 相位谱  
#     x: 数据  
#     **kwargs: 其他参数，如Fs, scale等  
  
# 65. plt.phase_spectrum(x, **kwargs) 相位谱  
#     x: 数据  
#     **kwargs: 其他参数，如Fs, scale等  
  
# 66. plt.xscale(value, **kwargs) 设置x轴的规度  
#     value: 规度类型，如'linear', 'log'等  
#     **kwargs: 其他参数，如basex, subsx等  
  
# 67. plt.yscale(value, **kwargs) 设置y轴的规度  
#     value: 规度类型，如'linear', 'log'等  
#     **kwargs: 其他参数，如basey, subsy等  
  
# 68. plt.xkcd(**kwargs) 手绘风格  
#     **kwargs: 其他参数，如scale, length等  
  
# 69. plt.axhline(y, **kwargs) 添加水平线  
#     y: y轴位置  
#     **kwargs: 其他参数，如color, linestyle等  
  
# 70. plt.axvline(x, **kwargs) 添加垂直线  
#     x: x轴位置  
#     **kwargs: 其他参数，如color, linestyle等  
  
# 71. plt.axhspan(ymin, ymax, **kwargs) 添加水平区域  
#     ymin: 区域下边界  
#     ymax: 区域上边界  
#     **kwargs: 其他参数，如color, alpha等  
  
# 72. plt.axvspan(xmin, xmax, **kwargs) 添加垂直区域  
#     xmin: 区域左边界  
#     xmax: 区域右边界  
#     **kwargs: 其他参数，如color, alpha等  
  
# 73. plt.broken_barh(xranges, yrange, **kwargs) 添加断续条形  
#     xranges: x轴范围列表  
#     yrange: y轴范围  
#     **kwargs: 其他参数，如color, edgecolor等  
  
# 74. plt.errorbar(x, y, yerr=None, xerr=None, **kwargs) 添加误差条  
#     x: x轴数据  
#     y: y轴数据  
#     yerr: y轴误差  
#     xerr: x轴误差  
#     **kwargs: 其他参数，如fmt, ecolor等  
  
# 75. plt.fill_betweenx(y, x1, x2=0, **kwargs) 填充两个y值之间  
#     y: y轴数据  
#     x1: 第一个函数的x轴数据  
#     x2: 第二个函数的x轴数据  
#     **kwargs: 其他参数，如color, alpha等  
  
# 76. plt.stackplot(x, *args, **kwargs) 堆叠图  
#     x: x轴数据  
#     *args: y轴数据  
#     **kwargs: 其他参数，如labels, colors等  
  
# 77. plt.violinplot(dataset, **kwargs) 小提琴图  
#     dataset: 数据集  
#     **kwargs: 其他参数，如vert, widths等  
  
# 78. plt.table(cellText, **kwargs) 表格  
#     cellText: 单元格文本  
#     **kwargs: 其他参数，如cellColours, colLabels等  
  
# 79. plt.triplot(x, y, triangles, **kwargs) 三角图  
#     x: x轴数据  
#     y: y轴数据  
#     triangles: 三角形顶点索引  
#     **kwargs: 其他参数，如color, linestyle等  
  
# 80. plt.barbs(x, y, u, v, **kwargs) 风羽图  
#     x: x轴数据  
#     y: y轴数据  
#     u: x方向速度  
#     v: y方向速度  
#     **kwargs: 其他参数，如length, pivot等  
  
# 81. plt.quiver(X, Y, U, V, **kwargs) 箭头图  
#     X: x轴数据  
#     Y: y轴数据  
#     U: x方向速度  
#     V: y方向速度  
#     **kwargs: 其他参数，如color, scale等  
  
# 82. plt.stackplot(x, *args, **kwargs) 堆叠图  
#     x: x轴数据  
#     *args: y轴数据  
#     **kwargs: 其他参数，如labels, colors等  
  
# 83. plt.psd(x, **kwargs) 功率谱密度  
#     x: 数据  
#     **kwargs: 其他参数，如NFFT, Fs等  
  
# 84. plt.specgram(x, **kwargs) 谱图  
#     x: 数据  
#     **kwargs: 其他参数，如NFFT, Fs等  
  
# 85. plt.cohere(x, y, **kwargs) 相干性  
#     x: x轴数据  
#     y: y轴数据  
#     **kwargs: 其他参数，如NFFT, Fs等  
  
# 86. plt.xcorr(x, y, **kwargs) 互相关  
#     x: x轴数据  
#     y: y轴数据  
#     **kwargs: 其他参数，如maxlags, normed等  
  
# 87. plt.magnitude_spectrum(x, **kwargs) 幅度谱  
#     x: 数据  
#     **kwargs: 其他参数，如Fs, scale等  
  
# 88. plt.angle_spectrum(x, **kwargs) 相位谱  
#     x: 数据  
#     **kwargs: 其他参数，如Fs, scale等  
  
# 89. plt.phase_spectrum(x, **kwargs) 相位谱  
#     x: 数据  
#     **kwargs: 其他参数，如Fs, scale等  
  
# 90. plt.xscale(value, **kwargs) 设置x轴的规度  
#     value: 规度类型，如'linear', 'log'等  
#     **kwargs: 其他参数，如basex, subsx等  
  
# 91. plt.yscale(value, **kwargs) 设置y轴的规度  
#     value: 规度类型，如'linear', 'log'等  
#     **kwargs: 其他参数，如basey, subsy等  
  
# 92. plt.xkcd(**kwargs) 手绘风格  
#     **kwargs: 其他参数，如scale, length等
```