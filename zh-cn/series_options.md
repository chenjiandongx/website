## ItemStyleOpts：图元样式配置项
> *class pyecharts.options.ItemStyleOpts*

```python
class ItemStyleOpts(
    # 图形的颜色。
    # 颜色可以使用 RGB 表示，比如 'rgb(128, 128, 128)'，如果想要加上 alpha 通道表示不透明度，
    # 可以使用 RGBA，比如 'rgba(128, 128, 128, 0.5)'，也可以使用十六进制格式，比如 '#ccc'。
    # 除了纯色之外颜色也支持渐变色和纹理填充
    # 
    # 线性渐变，前四个参数分别是 x0, y0, x2, y2, 范围从 0 - 1，相当于在图形包围盒中的百分比，
    # 如果 globalCoord 为 `true`，则该四个值是绝对的像素位置
    # color: {
    #    type: 'linear',
    #    x: 0,
    #    y: 0,
    #    x2: 0,
    #    y2: 1,
    #    colorStops: [{
    #        offset: 0, color: 'red' // 0% 处的颜色
    #    }, {
    #        offset: 1, color: 'blue' // 100% 处的颜色
    #    }],
    #    global: false // 缺省为 false
    # }
    # 
    # 径向渐变，前三个参数分别是圆心 x, y 和半径，取值同线性渐变
    # color: {
    #    type: 'radial',
    #    x: 0.5,
    #    y: 0.5,
    #    r: 0.5,
    #    colorStops: [{
    #        offset: 0, color: 'red' // 0% 处的颜色
    #    }, {
    #        offset: 1, color: 'blue' // 100% 处的颜色
    #    }],
    #    global: false // 缺省为 false
    # }
    # 
    # 纹理填充
    # color: {
    #    image: imageDom, // 支持为 HTMLImageElement, HTMLCanvasElement，不支持路径字符串
    #    repeat: 'repeat' // 是否平铺, 可以是 'repeat-x', 'repeat-y', 'no-repeat'
    # }
    color: Optional[str] = None,
    
    # 阴线 图形的颜色。
    color0: Optional[str] = None,

    # 图形的描边颜色。支持的颜色格式同 color，不支持回调函数。
    border_color: Optional[str] = None,
    
    # 阴线 图形的描边颜色。
    border_color0: Optional[str] = None,
    
    # 图形透明度。支持从 0 到 1 的数字，为 0 时不绘制该图形。
    opacity: Optional[Numeric] = None,
)
```

## TextStyleOpts：文字样式配置项
> *class pyecharts.options.TextStyleOpts*

```python
class TextStyleOpts(
    # 文字颜色。
    color: Optional[str] = None,

    # 文字字体的风格
    # 可选：'normal'，'italic'，'oblique'
    font_style: Optional[str] = None,

    # 主标题文字字体的粗细，可选：
    # 'normal'，'bold'，'bolder'，'lighter'
    font_weight: Optional[str] = None,

    # 文字的字体系列
    # 还可以是 'serif' , 'monospace', 'Arial', 'Courier New', 'Microsoft YaHei', ...
    font_family: Optional[str] = None,

    # 文字的字体大小
    font_size: Optional[Numeric] = None,

    # 行高
    line_height: Optional[str] = None,
)
```


## LabelOpts：标签配置项
> *class pyecahrts.options.LabelOpts*

```python
class LabelOpts(
    # 是否显示标签。
    is_show: bool = True,

    # 标签的位置。可选
    # 'top'，'left'，'right'，'bottom'，'inside'，'insideLeft'，'insideRight'
    # 'insideTop'，'insideBottom'， 'insideTopLeft'，'insideBottomLeft'
    # 'insideTopRight'，'insideBottomRight'
    position: Union[str, Sequence] = "top",

    # 文字的颜色。
    # 如果设置为 'auto'，则为视觉映射得到的颜色，如系列色。
    color: Optional[str] = None,

    # 文字的字体大小
    font_size: Numeric = 12,

    # 文字字体的风格，可选：
    # 'normal'，'italic'，'oblique'
    font_style: Optional[str] = None,

    # 文字字体的粗细，可选：
    # 'normal'，'bold'，'bolder'，'lighter'
    font_weight: Optional[str] = None,

    # 文字的字体系列
    # 还可以是 'serif' , 'monospace', 'Arial', 'Courier New', 'Microsoft YaHei', ...
    font_family: Optional[str] = None,

    # 标签旋转。从 -90 度到 90 度。正值是逆时针。
    rotate: Optional[Numeric] = None,

    # 文字水平对齐方式，默认自动。可选：
    # 'left'，'center'，'right'
    horizontal_align: Optional[str] = None,

    # 文字垂直对齐方式，默认自动。可选：
    # 'top'，'middle'，'bottom'
    vertical_align: Optional[str] = None,

    # 标签内容格式器，支持字符串模板和回调函数两种形式，字符串模板与回调函数返回的字符串均支持用 \n 换行。
    # 字符串模板 模板变量有：
    # {a}：系列名。
    # {b}：数据名。
    # {c}：数据值。
    # {@xxx}：数据中名为 'xxx' 的维度的值，如 {@product} 表示名为 'product'` 的维度的值。
    # {@[n]}：数据中维度 n 的值，如{@[3]}` 表示维度 3 的值，从 0 开始计数。
    # 示例：formatter: '{b}: {@score}'
    # 
    # 回调函数，回调函数格式：
    # (params: Object|Array) => string
    # 参数 params 是 formatter 需要的单个数据集。格式如下：
    # {
    #    componentType: 'series',
    #    // 系列类型
    #    seriesType: string,
    #    // 系列在传入的 option.series 中的 index
    #    seriesIndex: number,
    #    // 系列名称
    #    seriesName: string,
    #    // 数据名，类目名
    #    name: string,
    #    // 数据在传入的 data 数组中的 index
    #    dataIndex: number,
    #    // 传入的原始数据项
    #    data: Object,
    #    // 传入的数据值
    #    value: number|Array,
    #    // 数据图形的颜色
    #    color: string,
    # }
    formatter: Optional[str] = None,
)
```

## LineStyleOpts：线样式配置项
> *class pyecahrts.options.LineStyleOpts*

```python
class LineStyleOpts(
    # 线宽。
    width: Numeric = 1,

    # 图形透明度。支持从 0 到 1 的数字，为 0 时不绘制该图形。
    opacity: Numeric = 1,

    # 线的弯曲度，0 表示完全不弯曲
    curve: Numeric = 0,

    # 线的类型。可选：
    # 'solid', 'dashed', 'dotted'
    type_: str = "solid",

    # 线的颜色。
    # 颜色可以使用 RGB 表示，比如 'rgb(128, 128, 128)'，如果想要加上 alpha 通道表示不透明度，
    # 可以使用 RGBA，比如 'rgba(128, 128, 128, 0.5)'，也可以使用十六进制格式，比如 '#ccc'。
    # 除了纯色之外颜色也支持渐变色和纹理填充
    # 
    # 线性渐变，前四个参数分别是 x0, y0, x2, y2, 范围从 0 - 1，相当于在图形包围盒中的百分比，
    # 如果 globalCoord 为 `true`，则该四个值是绝对的像素位置
    # color: {
    #    type: 'linear',
    #    x: 0,
    #    y: 0,
    #    x2: 0,
    #    y2: 1,
    #    colorStops: [{
    #        offset: 0, color: 'red' // 0% 处的颜色
    #    }, {
    #        offset: 1, color: 'blue' // 100% 处的颜色
    #    }],
    #    global: false // 缺省为 false
    # }
    # 
    # 径向渐变，前三个参数分别是圆心 x, y 和半径，取值同线性渐变
    # color: {
    #    type: 'radial',
    #    x: 0.5,
    #    y: 0.5,
    #    r: 0.5,
    #    colorStops: [{
    #        offset: 0, color: 'red' // 0% 处的颜色
    #    }, {
    #        offset: 1, color: 'blue' // 100% 处的颜色
    #    }],
    #    global: false // 缺省为 false
    # }
    # 
    # 纹理填充
    # color: {
    #    image: imageDom, // 支持为 HTMLImageElement, HTMLCanvasElement，不支持路径字符串
    #    repeat: 'repeat' // 是否平铺, 可以是 'repeat-x', 'repeat-y', 'no-repeat'
    # }
    color: Optional[str] = None,
)
```

## SplitLineOpts：分割线配置项
> *class pyecharts.options.SplitLineOpts*

```python
class SplitLineOpts(
    # 是否显示分割线
    is_show: bool = False,

    # 线风格配置项，参考 `series_options.SplitLineOpts`
    linestyle_opts: LineStyleOpts = LineStyleOpts()
)
```

## MarkPointItem：标记点数据项
> *class pyecharts.options.MarkPointItem*

```python
class MarkPointItem(
    # 标注名称。
    name: Optional[str] = None,

    # 特殊的标注类型，用于标注最大值最小值等。可选:
    # 'min' 最大值。
    # 'max' 最大值。
    # 'average' 平均值。
    type_: Optional[str] = None,

    # 在使用 type 时有效，用于指定在哪个维度上指定最大值最小值，可以是 
    # 0（xAxis, radiusAxis），
    # 1（yAxis, angleAxis），默认使用第一个数值轴所在的维度。
    value_index: Optional[Numeric] = None,

    # 在使用 type 时有效，用于指定在哪个维度上指定最大值最小值。这可以是维度的直接名称，
    # 例如折线图时可以是 x、angle 等、candlestick 图时可以是 open、close 等维度名称。
    value_dim: Optional[str] = None,

    # 标注的坐标。坐标格式视系列的坐标系而定，可以是直角坐标系上的 x, y，
    # 也可以是极坐标系上的 radius, angle。例如 [121, 2323]、['aa', 998]。
    coord: Optional[List] = None,

    # 相对容器的屏幕 x 坐标，单位像素。
    x: Optional[Numeric] = None,

    # 相对容器的屏幕 y 坐标，单位像素。
    y: Optional[Numeric] = None,

    # 标注值，可以不设。
    value: Optional[Numeric] = None,

    # 标记的图形。
    # ECharts 提供的标记类型包括 'circle', 'rect', 'roundRect', 'triangle', 
    # 'diamond', 'pin', 'arrow', 'none'
    # 可以通过 'image://url' 设置为图片，其中 URL 为图片的链接，或者 dataURI。
    symbol: Optional[str] = None,

    # 标记的大小，可以设置成诸如 10 这样单一的数字，也可以用数组分开表示宽和高，
    # 例如 [20, 10] 表示标记宽为 20，高为 10。
    symbol_size: Union[Numeric, List] = None,
)
```

## MarkPointOpts：标记点配置项
> *class pyecahrts.options.MarkPointOpts*

```python
class MarkPointOpts(
    # 标记点数据，参考 `series_options.MarkPointItem`
    data: List[Union[MarkPointItem, dict]] = None,

    # 标记的图形。
    # ECharts 提供的标记类型包括 'circle', 'rect', 'roundRect', 'triangle', 
    # 'diamond', 'pin', 'arrow', 'none'
    # 可以通过 'image://url' 设置为图片，其中 URL 为图片的链接，或者 dataURI。
    symbol: Optional[str] = None,

    # 标记的大小，可以设置成诸如 10 这样单一的数字，也可以用数组分开表示宽和高，
    # 例如 [20, 10] 表示标记宽为 20，高为 10。
    # 如果需要每个数据的图形大小不一样，可以设置为如下格式的回调函数：
    # (value: Array|number, params: Object) => number|Array
    # 其中第一个参数 value 为 data 中的数据值。第二个参数 params 是其它的数据项参数。
    symbol_size: Union[None, Numeric] = None,

    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: LabelOpts = LabelOpts(position="inside", color="#fff"),
)
```

## MarkLineItem：标记线数据项
> *class pyecharts.options.MarkLineItem*

```python
class MarkLineItem(
    # 标注名称。
    name: Optional[str] = None,

    # 特殊的标注类型，用于标注最大值最小值等。可选:
    # 'min' 最大值。
    # 'max' 最大值。
    # 'average' 平均值。
    type_: Optional[str] = None,

    # 相对容器的屏幕 x 坐标，单位像素。
    x: Union[str, Numeric, None] = None,

    # 相对容器的屏幕 y 坐标，单位像素。
    y: Union[str, Numeric, None] = None,

    # 在使用 type 时有效，用于指定在哪个维度上指定最大值最小值，可以是 
    # 0（xAxis, radiusAxis），
    # 1（yAxis, angleAxis），默认使用第一个数值轴所在的维度。
    value_index: Optional[Numeric] = None,

    # 在使用 type 时有效，用于指定在哪个维度上指定最大值最小值。这可以是维度的直接名称，
    # 例如折线图时可以是 x、angle 等、candlestick 图时可以是 open、close 等维度名称。
    value_dim: Optional[str] = None,

    # 起点或终点的坐标。坐标格式视系列的坐标系而定，可以是直角坐标系上的 x, y，
    # 也可以是极坐标系上的 radius, angle。
    coord: Optional[Sequence] = None,

    # 终点标记的图形。
    # ECharts 提供的标记类型包括 'circle', 'rect', 'roundRect', 'triangle',
    #  'diamond', 'pin', 'arrow', 'none'
    # 可以通过 'image://url' 设置为图片，其中 URL 为图片的链接，或者 dataURI。
    symbol: Optional[str] = None,

    # 标记的大小，可以设置成诸如 10 这样单一的数字，也可以用数组分开表示宽和高，
    # 例如 [20, 10] 表示标记宽为 20，高为 10。
    symbol_size: Optional[Numeric] = None,
)
```

## MarkLineOpts：标记线配置项
> *class pyecharts.options.MarkLineOpts*

```python
class MarkLineOpts(
    # 图形是否不响应和触发鼠标事件，默认为 false，即响应和触发鼠标事件。
    is_silent: bool = False,

    # 标记线数据，参考 `series_options.MarkPointItem`
    data: List[Union[MarkLineItem, dict]] = None,

    # 标线两端的标记类型，可以是一个数组分别指定两端，也可以是单个统一指定，具体格式见 data.symbol。
    symbol: Optional[str] = None,

    # 标线两端的标记大小，可以是一个数组分别指定两端，也可以是单个统一指定。
    symbol_size: Union[None, Numeric] = None,
    
    # 标线数值的精度，在显示平均值线的时候有用。
    precision: int = 2,
    
    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: LabelOpts = LabelOpts(),
)
```

## MarkAreaItem: 标记区域数据项
> *class pyecharts.options.MarkAreaItem*

```python
class MarkAreaItem(
    # 区域名称, 仅仅就是一个名称而已
    name: Optional[str] = None,
    
    # 特殊的标注类型，用于标注最大值最小值等。
    # 'min' 最大值。
    # 'max' 最大值。
    # 'average' 平均值。
    type_: Tuple[Optional[str], Optional[str]] = (None, None),
    
    # 在使用 type 时有效，用于指定在哪个维度上指定最大值最小值，可以是 0（xAxis, radiusAxis），1（yAxis, angleAxis）。
    # 默认使用第一个数值轴所在的维度。
    value_index: Tuple[Optional[Numeric], Optional[Numeric]] = (None, None),
    
    # 在使用 type 时有效，用于指定在哪个维度上指定最大值最小值。
    # 这可以是维度的直接名称，例如折线图时可以是 x、angle 等、candlestick 图时可以是 open、close 等维度名称。
    value_dim: Tuple[Optional[str], Optional[str]] = (None, None),
    
    # 相对容器的屏幕 x 坐标，单位像素，支持百分比形式，例如 '20%'。
    x: Tuple[Union[str, Numeric, None], Union[str, Numeric, None]] = (None, None),
    
    # 相对容器的屏幕 y 坐标，单位像素，支持百分比形式，例如 '20%'。
    y: Tuple[Union[str, Numeric, None], Union[str, Numeric, None]] = (None, None),
    
    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: Union[LabelOpts, dict, None] = None,
    
    # 该数据项区域的样式，起点和终点项的 itemStyle 会合并到一起。参考 `series_options.ItemStyleOpts`
    itemstyle_opts: Union[ItemStyleOpts, dict, None] = None,
)
```

## MarkAreaOpts: 标记区域配置项
> *class pyecharts.options.MarkAreaOpts*

```python
class MarkAreaOpts(
    # 图形是否不响应和触发鼠标事件，默认为 false，即响应和触发鼠标事件。
    is_silent: bool = False,
    
    # 标签配置项，参考 `series_options.LabelOpts`
    label_opts: LabelOpts = LabelOpts(),
    
    # 标记区域数据，参考 `series_options.MarkAreaItem`
    data: List[Union[MarkAreaItem, dict]] = None,
)
```

## EffectOpts：涟漪特效配置项
> *class pyecharts.EffectOpts.EffectOpts*

```python
class EffectOpts(
    is_show: bool = True,
    brush_type: str = "stroke",
    scale: Numeric = 2.5,
    period: Numeric = 4,
    color: Optional[str] = None,
    symbol: Optional[str] = None,
    symbol_size: Optional[Numeric] = None,
)
```

## AreaStyleOpts：区域填充样式配置项
> *class pyecharts.options.AreaStyleOpts*

```python
class AreaStyleOpts(
    # 图形透明度。支持从 0 到 1 的数字，为 0 时不绘制该图形。
    opacity: Optional[Numeric] = 0,
    # 填充的颜色。
    # 颜色可以使用 RGB 表示，比如 'rgb(128, 128, 128)'，如果想要加上 alpha 通道表示不透明度，
    # 可以使用 RGBA，比如 'rgba(128, 128, 128, 0.5)'，也可以使用十六进制格式，比如 '#ccc'。
    # 除了纯色之外颜色也支持渐变色和纹理填充
    # 
    # 线性渐变，前四个参数分别是 x0, y0, x2, y2, 范围从 0 - 1，相当于在图形包围盒中的百分比，
    # 如果 globalCoord 为 `true`，则该四个值是绝对的像素位置
    # color: {
    #    type: 'linear',
    #    x: 0,
    #    y: 0,
    #    x2: 0,
    #    y2: 1,
    #    colorStops: [{
    #        offset: 0, color: 'red' // 0% 处的颜色
    #    }, {
    #        offset: 1, color: 'blue' // 100% 处的颜色
    #    }],
    #    global: false // 缺省为 false
    # }
    # 
    # 径向渐变，前三个参数分别是圆心 x, y 和半径，取值同线性渐变
    # color: {
    #    type: 'radial',
    #    x: 0.5,
    #    y: 0.5,
    #    r: 0.5,
    #    colorStops: [{
    #        offset: 0, color: 'red' // 0% 处的颜色
    #    }, {
    #        offset: 1, color: 'blue' // 100% 处的颜色
    #    }],
    #    global: false // 缺省为 false
    # }
    # 
    # 纹理填充
    # color: {
    #    image: imageDom, // 支持为 HTMLImageElement, HTMLCanvasElement，不支持路径字符串
    #    repeat: 'repeat' // 是否平铺, 可以是 'repeat-x', 'repeat-y', 'no-repeat'
    # }
    color: Optional[str] = None
)
```

## SplitAreaOpts：分隔区域配置项
> *class pyecharts.options.SplitAreaOpts*

```python
class SplitAreaOpts(
    # 是否显示分隔区域。
    is_show=True, 
    # 分隔区域的样式配置项，参考 `series_options.AreaStyleOpts`
    areastyle_opts: AreaStyleOpts = AreaStyleOpts()
)
```
