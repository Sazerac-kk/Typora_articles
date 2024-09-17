[**matplotlib.pyplot**](https://matplotlib.org/stable/api/pyplot_summary.html#module-matplotlib.pyplot)是 matplotlib 的基于状态的接口。它提供了一种隐式的、类似 MATLAB 的绘图方式。它还会在屏幕上打开图形，并充当图形 GUI 管理器。

## 1、显示窗口和隐式窗口

1）pyplot 主要用于交互式绘图和程序化绘图生成的简单情况，而对于复杂绘图，建议使用显示的面向对象的API，此时pyplot用于创建图形有一集图形中的轴。

2）请参阅[**pyplot.figure**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.figure.html#matplotlib.pyplot.figure)、[**pyplot.subplots**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.subplots.html#matplotlib.pyplot.subplots)、 和 [**pyplot.subplot_mosaic**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.subplot_mosaic.html#matplotlib.pyplot.subplot_mosaic)创建图形，以及 [轴 API](https://matplotlib.org/stable/api/axes_api.html)以了解轴上的绘图方法。有关隐式接口和显式接口之间权衡的说明，请参阅[Matplotlib 应用程序接口 (API) 。](https://matplotlib.org/stable/users/explain/figure/api_interfaces.html#api-interfaces)

## 2、管理图像和轴

### 1)axes:将Axes添加到当前图形并使其成为当前Axes。

Call signatures:

![img](data:image/png;base64,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)

Parameters:

**arg : None or 4-tuple**

​	None:一个用subplot(**kwargs)生成的新的窗口Axes

​	4-tuple : rect = (left, bottom, width, height)，以此为标准创建了一个新的轴。

**Projection:{None, 'aitoff', 'hammer', 'lambert', 'mollweide', 'polar', 'rectilinear', str}**

​	可选的投影类型，None代表直线

​	详情见：[**projections**](https://matplotlib.org/stable/api/projections_api.html#module-matplotlib.projections)

​	`matplotlib.projections.get_projection_names()`返回当前注册的所有投影的名称

**Polar: bool, default ,:False   # 极性**

​	如果为True 代表投影=‘极坐标’

**Sharex, sharey: Axes ,可选：**

​	axis与 sharex 和/或 sharey共享 x 或 y 。该轴将具有与共享轴相同的限制、刻度和比例。

Label: str

​	Axes返回的标签

Return：

​	Axes或者子类Axes：

​	返回的类型取决于projection，直线：Axes; 极坐标：projections.polar.PolarAxes

其他参数：

​	**kwargs：详情请见**[axes](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.axes.html#matplotlib.pyplot.axes)

### 2）其他:

| [**axes**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.axes.html#matplotlib.pyplot.axes) | 将 Axes  添加到当前图形并使其成为当前 Axes。                 |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [**cla**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.cla.html#matplotlib.pyplot.cla) | 清除当前轴。                                                 |
| [**clf**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.clf.html#matplotlib.pyplot.clf) | 清除当前数字。                                               |
| [**close**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.close.html#matplotlib.pyplot.close) | 关闭图形窗口。                                               |
| [**delaxes**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.delaxes.html#matplotlib.pyplot.delaxes) | [**Axes**](https://matplotlib.org/stable/api/_as_gen/matplotlib.axes.Axes.html#matplotlib.axes.Axes)从图中删除一个（默认为当前轴）。 |
| [**fignum_exists**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.fignum_exists.html#matplotlib.pyplot.fignum_exists) | 返回给定 id  的图窗是否存在。                                |
| [**figure**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.figure.html#matplotlib.pyplot.figure) | 创建新图窗，或激活现有图窗。                                 |
| [**gca**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.gca.html#matplotlib.pyplot.gca) | 获取当前的轴。                                               |
| [**gcf**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.gcf.html#matplotlib.pyplot.gcf) | 获取当前数字。                                               |
| [**get_figlabels**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.get_figlabels.html#matplotlib.pyplot.get_figlabels) | 返回现有图形标签的列表。                                     |
| [**get_fignums**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.get_fignums.html#matplotlib.pyplot.get_fignums) | 返回现有图号的列表。                                         |
| [**sca**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.sca.html#matplotlib.pyplot.sca) | 将当前 Axes 设置为*ax*并将当前Figure 设置为*ax*的父级。      |
| [**subplot**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.subplot.html#matplotlib.pyplot.subplot) | 将轴添加到当前图形或检索现有轴。                             |
| [**subplot2grid**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.subplot2grid.html#matplotlib.pyplot.subplot2grid) | 在常规网格内的特定位置创建子图。                             |
| [**subplot_mosaic**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.subplot_mosaic.html#matplotlib.pyplot.subplot_mosaic) | 基于 ASCII  艺术或嵌套列表构建轴布局。                       |
| [**subplots**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.subplots.html#matplotlib.pyplot.subplots) | 创建一个图形和一组子图。                                     |
| [**twinx**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.twinx.html#matplotlib.pyplot.twinx) | 制作并返回共享*x*轴的第二个轴。                              |
| [**twiny**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.twiny.html#matplotlib.pyplot.twiny) | 创建并返回共享*y*轴的第二个轴。                              |

## 3、将数据添加到图中

基本：

| [**plot**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.plot.html#matplotlib.pyplot.plot) | 将 y 与 x  绘制为线条和/或标记。             |
| ------------------------------------------------------------ | -------------------------------------------- |
| [**errorbar**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.errorbar.html#matplotlib.pyplot.errorbar) | 将 y 与 x  绘制为带有误差条的线条和/或标记。 |
| [**scatter**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.scatter.html#matplotlib.pyplot.scatter) | *y*与y的散点图                               |
| [**plot_date**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.plot_date.html#matplotlib.pyplot.plot_date) | [*不鼓励*] 绘制强制轴将浮点数视为日期的图。  |
| [**step**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.step.html#matplotlib.pyplot.step) | 制作一个步骤图。                             |
| [**loglog**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.loglog.html#matplotlib.pyplot.loglog) | 在 x 轴和 y  轴上绘制对数缩放图。            |
| [**semilogx**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.semilogx.html#matplotlib.pyplot.semilogx) | 在 x  轴上绘制对数缩放图。                   |
| [**semilogy**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.semilogy.html#matplotlib.pyplot.semilogy) | 在 y  轴上绘制对数缩放图。                   |
| [**fill_between**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.fill_between.html#matplotlib.pyplot.fill_between) | 填充两条水平曲线之间的区域。                 |
| [**fill_betweenx**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.fill_betweenx.html#matplotlib.pyplot.fill_betweenx) | 填充两条垂直曲线之间的区域。                 |
| [**bar**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.bar.html#matplotlib.pyplot.bar) | 绘制条形图。                                 |
| [**barh**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.barh.html#matplotlib.pyplot.barh) | 绘制水平条形图。                             |
| [**bar_label**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.bar_label.html#matplotlib.pyplot.bar_label) | 标记条形图。                                 |
| [**stem**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.stem.html#matplotlib.pyplot.stem) | 创建一个茎图。                               |
| [**eventplot**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.eventplot.html#matplotlib.pyplot.eventplot) | 在给定位置绘制相同的平行线。                 |
| [**pie**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.pie.html#matplotlib.pyplot.pie) | 绘制饼图。                                   |
| [**stackplot**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.stackplot.html#matplotlib.pyplot.stackplot) | 绘制堆积面积图。                             |
| [**broken_barh**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.broken_barh.html#matplotlib.pyplot.broken_barh) | 绘制矩形的水平序列。                         |
| [**vlines**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.vlines.html#matplotlib.pyplot.vlines) | *在每个x 处*绘制从*ymin*到*ymax 的*垂直线。  |
| [**hlines**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.hlines.html#matplotlib.pyplot.hlines) | *在每个y 处*绘制从*xmin*到*xmax 的*水平线。  |
| [**fill**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.fill.html#matplotlib.pyplot.fill) | 绘制填充多边形。                             |
| [**polar**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.polar.html#matplotlib.pyplot.polar) | 绘制极坐标图。                               |

 

二维数组：

| [**imshow**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.imshow.html#matplotlib.pyplot.imshow) | 将数据显示为图像，即在二维规则光栅上。 |
| ------------------------------------------------------------ | -------------------------------------- |
| [**matshow**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.matshow.html#matplotlib.pyplot.matshow) | 在新的图窗窗口中将数组显示为矩阵。     |
| [**pcolor**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.pcolor.html#matplotlib.pyplot.pcolor) | 使用不规则矩形网格创建伪彩色图。       |
| [**pcolormesh**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.pcolormesh.html#matplotlib.pyplot.pcolormesh) | 使用不规则矩形网格创建伪彩色图。       |
| [**spy**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.spy.html#matplotlib.pyplot.spy) | 绘制二维数组的稀疏模式。               |
| [**figimage**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.figimage.html#matplotlib.pyplot.figimage) | 将未重新采样的图像添加到图中。         |

 

 

文本和注释：

| [**annotate**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.annotate.html#matplotlib.pyplot.annotate) | 用文本*text*注释点*xy*。                                     |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [**text**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.text.html#matplotlib.pyplot.text) | 将文本添加到轴。                                             |
| [**figtext**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.figtext.html#matplotlib.pyplot.figtext) | 向图中添加文本。                                             |
| [**table**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.table.html#matplotlib.pyplot.table) | 将表添加到[**Axes**](https://matplotlib.org/stable/api/_as_gen/matplotlib.axes.Axes.html#matplotlib.axes.Axes). |
| [**arrow**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.arrow.html#matplotlib.pyplot.arrow) | 向轴添加箭头。                                               |
| [**figlegend**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.figlegend.html#matplotlib.pyplot.figlegend) | 在图上放置图例。                                             |
| [**legend**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.legend.html#matplotlib.pyplot.legend) | 在轴上放置一个图例。                                         |

 

 

## 4、轴配置：

| [**autoscale**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.autoscale.html#matplotlib.pyplot.autoscale) | 根据数据自动缩放轴视图（切换）。                             |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [**axis**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.axis.html#matplotlib.pyplot.axis) | 获取或设置某些轴属性的便捷方法。                             |
| [**box**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.box.html#matplotlib.pyplot.box) | 打开或关闭当前轴上的轴框。                                   |
| [**grid**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.grid.html#matplotlib.pyplot.grid) | 配置网格线。                                                 |
| [**locator_params**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.locator_params.html#matplotlib.pyplot.locator_params) | 主要蜱虫定位器的控制行为。                                   |
| [**minorticks_off**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.minorticks_off.html#matplotlib.pyplot.minorticks_off) | 删除轴上的小刻度。                                           |
| [**minorticks_on**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.minorticks_on.html#matplotlib.pyplot.minorticks_on) | 在轴上显示小刻度。                                           |
| [**rgrids**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.rgrids.html#matplotlib.pyplot.rgrids) | 获取或设置当前极坐标图上的径向网格线。                       |
| [**thetagrids**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.thetagrids.html#matplotlib.pyplot.thetagrids) | 获取或设置当前极坐标图上的  theta 网格线。                   |
| [**tick_params**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.tick_params.html#matplotlib.pyplot.tick_params) | 更改刻度、刻度标签和网格线的外观。                           |
| [**ticklabel_format**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.ticklabel_format.html#matplotlib.pyplot.ticklabel_format) | 配置[**ScalarFormatter**](https://matplotlib.org/stable/api/ticker_api.html#matplotlib.ticker.ScalarFormatter)线性轴的默认使用。 |
| [**xlabel**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.xlabel.html#matplotlib.pyplot.xlabel) | 设置 x 轴的标签。                                            |
| [**xlim**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.xlim.html#matplotlib.pyplot.xlim) | 获取或设置当前轴的 x  限制。                                 |
| [**xscale**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.xscale.html#matplotlib.pyplot.xscale) | 设置 x 轴的比例。                                            |
| [**xticks**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.xticks.html#matplotlib.pyplot.xticks) | 获取或设置 x  轴的当前刻度位置和标签。                       |
| [**ylabel**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.ylabel.html#matplotlib.pyplot.ylabel) | 设置 y 轴的标签。                                            |
| [**ylim**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.ylim.html#matplotlib.pyplot.ylim) | 获取或设置当前轴的 y  限制。                                 |
| [**yscale**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.yscale.html#matplotlib.pyplot.yscale) | 设置 y 轴的比例。                                            |
| [**yticks**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.yticks.html#matplotlib.pyplot.yticks) | 获取或设置 y  轴的当前刻度位置和标签。                       |
| [**suptitle**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.suptitle.html#matplotlib.pyplot.suptitle) | 向图中添加居中的副标题。                                     |
| [**title**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.title.html#matplotlib.pyplot.title) | 为轴设置标题。                                               |

 

 

## 5、布局：

| [**margins**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.margins.html#matplotlib.pyplot.margins) | 设置或检索自动缩放边距。       |
| ------------------------------------------------------------ | ------------------------------ |
| [**subplots_adjust**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.subplots_adjust.html#matplotlib.pyplot.subplots_adjust) | 调整子图布局参数。             |
| [**subplot_tool**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.subplot_tool.html#matplotlib.pyplot.subplot_tool) | 启动图形的子图工具窗口。       |
| [**tight_layout**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.tight_layout.html#matplotlib.pyplot.tight_layout) | 调整子图之间和子图周围的填充。 |

 

 

## 6、颜色映射：

| [**clim**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.clim.html#matplotlib.pyplot.clim) | 设置当前图像的颜色限制。                                |
| ------------------------------------------------------------ | ------------------------------------------------------- |
| [**colorbar**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.colorbar.html#matplotlib.pyplot.colorbar) | 将颜色条添加到绘图中。                                  |
| [**gci**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.gci.html#matplotlib.pyplot.gci) | 获取当前的可着色艺术家。                                |
| [**sci**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.sci.html#matplotlib.pyplot.sci) | 设置当前图像。                                          |
| [**get_cmap**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.get_cmap.html#matplotlib.pyplot.get_cmap) | 获取一个颜色图实例，如果*name*为 None，则默认为 rc 值。 |
| [**set_cmap**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.set_cmap.html#matplotlib.pyplot.set_cmap) | 设置默认颜色图，并将其应用到当前图像（如果有）。        |
| [**imread**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.imread.html#matplotlib.pyplot.imread) | 将图像从文件读取到数组中。                              |
| [**imsave**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.imsave.html#matplotlib.pyplot.imsave) | 颜色映射并将数组保存为图像文件。                        |

 

## 7、输出：

| [**draw**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.draw.html#matplotlib.pyplot.draw) | 重新绘制当前图形。                 |
| ------------------------------------------------------------ | ---------------------------------- |
| [**draw_if_interactive**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.draw_if_interactive.html#matplotlib.pyplot.draw_if_interactive) | 如果处于交互模式，则重绘当前图形。 |
| [**ioff**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.ioff.html#matplotlib.pyplot.ioff) | 禁用交互模式。                     |
| [**ion**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.ion.html#matplotlib.pyplot.ion) | 启用交互模式。                     |
| [**install_repl_displayhook**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.install_repl_displayhook.html#matplotlib.pyplot.install_repl_displayhook) | 连接到当前shell的显示钩子。        |
| [**isinteractive**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.isinteractive.html#matplotlib.pyplot.isinteractive) | 返回每个绘图命令后是否更新绘图。   |
| [**pause**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.pause.html#matplotlib.pyplot.pause) | 将 GUI 事件循环运行*间隔*秒。      |
| [**savefig**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.savefig.html#matplotlib.pyplot.savefig) | 保存当前图形。                     |
| [**show**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.show.html#matplotlib.pyplot.show) | 显示所有开放数字。                 |
| [**switch_backend**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.switch_backend.html#matplotlib.pyplot.switch_backend) | 设置 pyplot  后端。                |
| [**uninstall_repl_displayhook**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.uninstall_repl_displayhook.html#matplotlib.pyplot.uninstall_repl_displayhook) | 与当前 shell  的显示挂钩断开连接。 |

 

## 8、其他详见：

<https://matplotlib.org/stable/api/pyplot_summary.html>