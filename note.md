# 01-内容

1. 基于flexible.js+rem智能大屏适配
2. vscode cssrem插件 easyless插件
3. flex布局
4. less使用
5. 基于echarts数据可视化展示
6. echarts柱状图数据设置
7. echarts地图引入

# 02-数据可视化介绍

# 03-可视化适配方案

html中：

```html
<link rel="stylesheet" href="css/index.css" />
<body>
    // 在html中引入less文件必须下载less，才能好使
    <script src="https://cdnjs.cloudflare.com/ajax/libs/less.js/2.5.3/less.min.js"></script>
    // 引入flexible
    <script src="http://g.tbcdn.cn/mtb/lib-flexible/0.3.2/??flexible_css.js,flexible.js"></script>
    <script src="js/flexible.js"></script>
</body>
```

css/index.less中：

```less
* {
    padding: 0;
    margin: 0;
    box-sizing: border-box
}
```

js/flexible.js中：

```js
setRemUnit() {
    /24
}
```

cssrem插件点击设置，Root Font Size手动改成80

重启vscode

# 04-可视化项目头部制作

css/index.less中：

```less
body {
    background: url(../images/bg.jpg) no-repeat top center;
    line-height: 1.15;
}
header {
    position: relative;
    height: 100px;
    background: url(../images/head_bg.png) no-repeat;
    background-size: 100% 100%;
    h1 {
        font-size: 0.475rem;
        color: #fff;
        text-align: center;
        line-height: 1rem;
    }
    .showTime {
        position: absolute;
        right: 0.375rem;
        top: 0;
        line-height: 0.9375rem;
        color: rgba(255, 255, 255, 0.7);
        font-size: 20px
    }
}
```

index.html中：

```html
<body>
    <header>
        <h1>
            数据可视化-ECharts
        </h1>
        <div class="showTime">
            
        </div>
    </header>
    <script>
        // 放入获取当前时间的js代码
        // 把获取到的时间插入到showTime的盒子中
    </script>
    <script src="js/flexible.js"></script>
</body>
```

# 05-mainbox布局分析

index.html中：

```html
<section class="mainbox">
    <div class="column">
        
    </div>
    <div class="column">
        
    </div>
    <div class="column">
        
    </div>
</section>
<script src="js/flexible.js"></script>
```

css/index.less中：

```less
.mainbox {
    display: flex;
    min-width: 1024px;
    max-width: 1920px;
    margin: 0 auto;
    padding: 10px 10px 0;
    .column {
        flex: 3;
    }
    .column:nth-child(2) {
        flex: 5;
    }
}
```

# 06-panel盒子公共面板

index.html中：

```html
<section class="mainbox">
    <div class="column">
        <div class="panel">
            <div cladd="panel-footer">
                
            </div>
        </div>
    </div>
    <div class="column">
        
    </div>
    <div class="column">
        
    </div>
</section>
```

css/index.less中：

```less
.mainbox {
    display: flex;
    min-width: 1024px;
    max-width: 1920px;
    margin: 0 auto;
    padding: 10px 10px 0;
    .column {
        flex: 3;
    }
    .column:nth-child(2) {
        flex: 5;
    }
    .panel {
        position: relative;
        height: 3.875rem;
        border: 1px solid rgba(25, 186, 139, 0.17);
        background: url(../images/line\(1\).png) rgba(255, 255, 255, 0.03);
        padding: 0 15px 40px;
        margin-bottom: 15px;
        &::before {
            position: absolute;
            top: 0;
            left: 0;
            width: 10px;
            height: 10px;
            border-left: 2px solid #02a6b5;
            border-top: 2px solid #02a6b5;
        }
        &::after {
            position: absolute;
            top: 0;
            left: 0;
            width: 10px;
            height: 10px;
            border-right: 2px solid #02a6b5;
            border-top: 2px solid #02a6b5;
        }
        .panel-footer {
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            &::before {
                position: absolute;
                top: 0;
                left: 0;
                width: 10px;
                height: 10px;
                border-left: 2px solid #02a6b5;
                border-bottom: 2px solid #02a6b5;
                content: ''
            }
            &::after {
                position: absolute;
                top: 0;
                left: 0;
                width: 10px;
                height: 10px;
                border-right: 2px solid #02a6b5;
                border-bottom: 2px solid #02a6b5;
                content: ''
            }
        }
    }
}
```

# 07-panel盒子完成

index.html中：

```html
<div class="column">
    <div class="panel bar">
        <h2>
            柱形图-就业行业
        </h2>
        <div class="chart">
            
        </div>
        <div cladd="panel-footer"></div>
    </div>
    <div class="panel line">
        <h2>
            柱形图-就业行业
        </h2>
        <div class="chart">
            
        </div>
        <div cladd="panel-footer"></div>
    </div>
    <div class="panel pie">
        <h2>
            柱形图-就业行业
        </h2>
        <div class="chart">
            
        </div>
        <div cladd="panel-footer"></div>
    </div>
</div>
```

复制该代码到右边的盒子里

css/index.less中：

```css
.panel {
    h2 {
        height: 0.6rem;
        color: #fff;
        line-height: 48px;
        font-size: 0.25rem;
        font-weight: 400;
    }
    .chart {
        height: 3rem;
        
    }
}
```

# 08-数字模块no布局制作（中间模块布局）

index.html中：

```html
<div class="column">
    <div class="no">
        
    </div>
</div>
```

css/index.less中：

```css
.column:nth-child(2) {
    flex: 5;
    margin: 0 0.125rem 0.875rem;
}
.no {
    background: url(101, 132, 266, 0.1);
    padding: 0.1875rem;
}
```

# 09-no-hd模块详细布局

index.html中：

```html
<div class="column">
    <div class="no">
        <div class="no-hd">
            <ul>
                <li>123456</li>
                <li>123456</li>
            </ul>
        </div>
        <div class="no-bd">
            
        </div>
    </div>
</div>
```

css/index.less中：

```css
li: {
    list-style: none;
}
// 声明字体
@font-face {
    font-family: electronicFont;
    src: url(../font/DS-DIGIT.TTF)
}
.no {
    background: url(101, 132, 266, 0.1);
    padding: 0.1875rem;
    .no-hd {
        position: relative;
        border: 1px solid rgba(25, 186, 139, 0.17);
        &::before {
            position: absolute;
            top: 0;
            left: 0;
            width: 30px;
            height: 10px;
            border-left: 2px solid #02a6b5;
            border-top: 2px solid #02a6b5;
            content: ''
        }
        &::after {
            position: absolute;
            top: 0;
            left: 0;
            width: 30px;
            height: 10px;
            border-right: 2px solid #02a6b5;
            border-bottom: 2px solid #02a6b5;
            content: ''
        }
        ul {
            display: flex;
            li: {
                position: relative;
                flex: 1;
                line-height: 80px;
                font-size: 70px;
                color: #ffeb7b;
                font-family: "electronicFont";
                :nth-child(1)::after {
                    content: '';
                    position: absolute;
                    top: 25%;
                    right: 0;
                    height: 50%;
                    width: 1px;
                    background: rgba(255, 255, 255, 0.2);
                }
            }
        }
    }
}
```

新建文件夹font/数字字体

# 10-no-bd模块详细布局

index.html中：

```html
<div class="no-hd">
    <ul>
        <li>123456</li>
        <li>123456</li>
    </ul>
</div>
<div class="no-bd">
    <ul>
        <li>前端需求人数</li>
        <li>市场供应人数</li>
    </ul>     
</div>
```

css/index.less中：

```css
.no-hd {
}
.no-bd {
    ul {
        display: flex;
        li {
            flex: 1;
            text-align: center;
            color: rgba(255, 255, 255, 0.7);
            font-size: 0.225rem;
            height: 0.5rem;
            line-height: 0.5rem;
            padding-top: 10px;
        }
    }
}
```

# 11-map1球体模块制作

index.html中：

```html
<div class="no">
</div>
<div class="map">
    <div class="map1">
        
    </div>
</div>
```

css/index.less中：

```css
.map {
    position: relative;
    height: 10.125rem;
    .map1 {
        width: 6.475rem;
        height: 6.475rem;
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        background: url(../images/map.png);
        background-size: 100% 100%;
        opacity: 0.3;
    }
}
```

# 12-map2模块旋转球体制作

index.html中：

```html
<div class="map1">
</div>
<div class="map2">
</div>
```

css/index.less中：

```css
.map1 {
}
.map2 {
    width: 8.0375rem;
    height: 8.0375rem;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background: url(../images/lbx.png);
    animation: rotate1 15s linear infinate;
    opacity: 0.6;
    background-size: 100% 100%;
}
@keyframes rotate1 {
    from {
        transform: translateX(-50%) translateY(-50%) rotate(0deg);
    }
    to {
        transform: translateX(-50%) translateY(-50%) rotate(360deg);
    }
}
```

# 13-map3模块旋转箭头制作

index.html中：

```html
<div class="map1">
</div>
<div class="map2">
</div>
<div class="map3">
</div>
<div class="chart">
</div>
```

css/index.less中：

```css
.map2 {
}
.map3 {
    width: 7.075rem;
    height: 7.075rem;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background: url(../images/jt.png);
    animation: rotate2 10s linear infinate;
    opacity: 0.6;
    background-size: 100% 100%;
}
.chart {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 10.125rem;
}
@keyframes rotate2 {
    from {
        transform: translate(-50% -50%) rotate(0deg);
    }
    to {
        transform: translate(-50% -50%) rotate(-360deg);
    }
}
```

# 14-ECharts简介

常见的数据可视化库：

1. D3.js(评价高 入手难)
2. ECharts(百度 开源)
3. Highcharts(国外的 不免费)
4. AntV(蚂蚁金服)
5.  Highcharts和Echarts像Office和WPS

# 15-体验使用五部曲

1. 下载并引入echarts.js
2. 准备一个具备大小的DOM容器
3. 初始化echarts实例对象
4. 指定配置项和数据
5. 将配置项设置给echarts实例对象

```html
<script src="echarts.min.js"></script>
<div id="main" style="width: 200px; height: 200px">
</div>
<script>
    // 基于准备好的dom，初始化echarts实例
        var myChart = echarts.init(document.getElementById('main'));

        // 指定图表的配置项和数据
        var option = {
            title: {
                text: 'ECharts 入门示例'
            },
            tooltip: {},
            legend: {
                data:['销量']
            },
            xAxis: {
                data: ["衬衫","羊毛衫","雪纺衫","裤子","高跟鞋","袜子"]
            },
            yAxis: {},
            series: [{
                name: '销量',
                type: 'bar',
                data: [5, 20, 36, 10, 10, 20]
            }]
        };

        // 使用刚指定的配置项和数据显示图表。
        myChart.setOption(option);
</script>
```

# 16-基础配置（上）

```js
// 指定图表的配置项和数据
        var option = {
            
            // 图表的标题
            title: {
                text: 'ECharts 入门示例'
            },
            
            // 提示框组件 鼠标放到折线的点上 会出现黑框 里边显示具体的数据（图表的提示框）
            tooltip: {
                // 触发方式（坐标轴）柱状图 饼图（item） 官网-》文档-》配置项手册
                trigger: 'axis'
            },
            
            // 图例组件 表的上方标识 什么颜色折线代表什么数据
            legend: {
                data:['销量']
            },
          
            // 工具箱组件 右上角有一个保存按钮 点击 把这张图表保存成一张图片
            toolbox: {
                feature: {
                    saveAsImage: {}
                }
            },
        };
```

# 17-基础配置（中）

```js
// 指定图表的配置项和数据
        var option = {
            
            // 网格配置 可以控制图表大小
            grid: {
                left: '3%',
                right: '4%',
                bottom: '3%',
                // 显示图表的刻度标签
                containLabel: true
            },
            
            // 设置x轴的相关配置
            xAxis: {
                // 类目
                type: 'category',
                // 是否让坐标轴和线条有缝隙
                boundaryGap: false,
                data: ["衬衫","羊毛衫","雪纺衫","裤子","高跟鞋","袜子"]
            },
            
            // 设置y轴的相关配置
            yAxis: {
                type: 'value',
            },
        };
```

# 18-基础配置（下）

```js
// 指定图表的配置项和数据
        var option = {
            
            color: ['pink', 'red', 'green', 'skyblue'],
            
            // 图例组件 表的上方标识 什么颜色折线代表什么数据
            legend: {
                // series里边如果name有值,则legend中的data可以删掉 
                data:['邮件营销', '视频广告']
            },
            
            // 系统图表配置 它决定了显示哪种类型的图表
            // 一共有2个对象 代表有俩条线
            // stack表示数据堆叠 第一个是5 下一个是5+5=10 而不是5 
            // 如果直接想展示data中的数据，把stack删掉就好了
            series: [
                {
                    name: '邮件营销',
                    type: 'line',
                    stack: '总量',
                    data: [5, 20, 36, 10, 10, 20]
            	},
                {
                    name: '视频广告',
                    type: 'line',
                    stack: '总量',
                    data: [5, 20, 36, 10, 10, 20]
            	},
            ]
        };
```

# 19-柱状图bar引入到HTML页面中

新建index.js中：

```js
// 柱状图模块1
(function() {
    var myChart = echarts.init(document.querySelector('.bar .chart'));
    var option = {
        color: ['#3398DB'],
        tooltip: {
            trigger: 'axis',
            axisPointer: {            // 坐标轴指示器，坐标轴触发有效
                type: 'shadow'        // 默认为直线，可选为：'line' | 'shadow'
            }
        },
        grid: {
            left: '3%',
            right: '4%',
            bottom: '3%',
            containLabel: true
        },
        xAxis: [
            {
                type: 'category',
                data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'],
                axisTick: {
                    alignWithLabel: true
                }
            }
        ],
        yAxis: [
            {
                type: 'value'
            }
        ],
        series: [
            {
                name: '直接访问',
                type: 'bar',
                barWidth: '60%',
                data: [10, 52, 200, 334, 390, 330, 220]
            }
        ]
    };
    myChart.setOption(option);
})();
```

index.html中：

```html
// 下载并引入echart
// 引入index.js文件
```

# 20-定制柱状图bar(上)

index.js中：

```js
color: ['#2f89cf'],
grid: {
    left: '0%',
    right: '0%',
    top: '10px',
    bottom: '4%',
    containLabel: true
},
xAxis: [
    {
        type: 'category',
        data: ['旅游行业', '教育培训', '游戏行业', '医疗行业', '电商行业', '社交行业', '金融行业'],
        axisTick: {
            alignWithLabel: true
        },
    	// 修改刻度标签相关样式
    	axisLabel: {
    		color: 'rgba(255, 255, 255, 0.6)';
    		fontSize: '12'
    	},
        // 不显示x坐标轴的样式
        axisLine: {
            show: false
        }
	}
],
```

# 21-定制柱状图bar(中)

index.js中：

```js
yAxis: [
    {
        type: 'value',
        // 修改刻度标签相关样式
    	axisLabel: {
    		color: 'rgba(255, 255, 255, 0.6)';
    		fontSize: 12
    	},
        // 修改y轴坐标样式
        axisLine: {
            lineStyle: {
                color: 'rgba(255, 255, 255, 0.1)',
                width: 2
            }
        },
        // 修改y轴分割线的颜色
        splitLine: {
            lineStyle: {
                color: 'rgba(255, 255, 255, 0.1)',
            }
        },
    }
],
```

# 21-定制柱状图bar(下)

index.js中：

```s
series: [
    {
        name: '直接访问',
        type: 'bar',
        barWidth: '35%',
        data: [10, 52, 200, 334, 390, 330, 220],
        itemStyle: {
         	// 修改柱子圆角
            barBorderRadius: 5
        }
    }
]
```

# 23-图表跟随屏幕缩放适配

index.js中：

```js
myChart.setOption(option);
window.addEventListener("resize", function() {
    myChart.resize()
})
```

# 24-柱形图2引入到html模板

index.js中：

```js
class="panel bar2"
// 柱状图模块2
(function() {
    var myColor = ['#1089E7', '#f57474', '#56d0e3', '#f8b448', '#8b78f6']
    var myChart = echarts.init(document.querySelector('.bar2 .chart'));
    var option = {
        grid: {
            left: '3%',
            right: '4%',
            bottom: '3%',
            // containLabel: true
        },
        xAxis: {
            type: 'value',
            boundaryGap: [0, 0.01]
        },
        yAxis: {
            type: 'category',
            data: ['巴西', '印尼', '美国', '印度', '中国', '世界人口(万)']
        },
        series: [
            {
                name: '2011年',
                type: 'bar',
                data: [18203, 23489, 29034, 104970, 131744, 630230]
            },
            {
                name: '2012年',
                type: 'bar',
                data: [19325, 23438, 31000, 121594, 134141, 681807]
            }
        ]
    };
    myChart.setOption(option);
})();
```

# 25-柱形图2定制1

index.js中：

```js
		grid: {
            left: '22%',
            top: '10%',
            bottom: '10%',
            containLabel: true
        },
        xAxis: {
            show: false
        },
        yAxis: {
            type: 'category',
            data: ['巴西', '印尼', '美国', '印度', '中国'],
            // 不显示y轴的线
            axisLine: {
                show: false
            },
            // 不显示刻度
            axisTick: {
                show: false
            },
            // 把刻度标签里的文字颜色
            axisLabel: {
                color: #fff
            }
        },
```

# 26-柱形图2定制2(带框的柱形图)

index.js中：

```js
		series: [
            {
                name: '条',
                type: 'bar',
                data: [18203, 23489, 29034, 104970, 131744, 630230]，
                // 修改第一个柱子的圆角
                itemStyle: {
                	barBorderRadius: 20
            	},
            	// 柱子之间的距离
            	barCategoryGap: 50,
            	// 柱子的宽度
            	barWidth: 10
            },
            {
                name: '2012年',
                type: 'bar',
                data: [19325, 23438, 31000, 121594, 134141, 681807]
            }
        ]
```

# 27-柱形图2定制3(带框的柱形图)

index.js中：

```js
		series: [
            {
                name: '条',
                type: 'bar',
                data: [18203, 23489, 29034, 104970, 131744, 630230]，
                // 修改第一个柱子的圆角
                itemStyle: {
                	barBorderRadius: 20
            	},
            	// 柱子之间的距离
            	barCategoryGap: 50,
            	// 柱子的宽度
            	barWidth: 10,
            	// 显示柱子内的文字
            	label: {
            		show: true,
            		position: 'inside',
            		// {c}会自动解析data里边的数据
            		formatter: "{c}%"
            	}
            },
            {
                name: '2012年',
                type: 'bar',
                data: [19325, 23438, 31000, 121594, 134141, 681807]
            }
        ]
```

# 28-柱形图2定制4(带框的柱形图)

index.js中：

```js
		series: [
            {
                name: '条',
                type: 'bar',
                data: [18203, 23489, 29034, 104970, 131744]，
                // 修改第一个柱子的圆角
                itemStyle: {
                	barBorderRadius: 20,
                	// 这里的color也可以修改柱子的颜色
                	color: function(params) {
            			return myColor[params.dataIndex]
            		}
            	},
            	// 柱子之间的距离
            	barCategoryGap: 50,
            	// 柱子的宽度
            	barWidth: 10,
            },
            {
                name: '框',
                type: 'bar',
                // 柱子之间的距离
            	barCategoryGap: 50,
            	// 柱子的宽度
            	barWidth: 15,
                data: [19325, 23438, 31000, 121594, 134141, 681807],
                // 修改第一个柱子的圆角
                itemStyle: {
                	barBorderRadius: 15,
                	// 这里的color也可以修改柱子的颜色
                	color: "none",
                    borderWidth: 3,
                    borderColor: '#00c1de'
            	},
            }
        ]
```

# 29-柱形图2定制5(带框的柱形图)

index.js中：

```js
	yAxis: [
        {
            type: 'category',
            data: ['HTML5', 'CSS3', 'javascript', 'VUE', 'NODE'],
            // 不显示y轴的线
            axisLine: {
                show: false
            },
            // 不显示刻度
            axisTick: {
                show: false
            },
            // 把刻度标签里的文字颜色
            axisLabel: {
                color: #fff
            }
        },
        {
            data: [702, 350, 610, 793, 664],
            // 不显示y轴的线
            axisLine: {
                show: false
            },
            // 不显示刻度
            axisTick: {
                show: false
            },
            // 把刻度标签里的文字颜色
            axisLabel: {
                color: #fff
            }
        },
    ]
```

# 30-柱形图2定制6(带框的柱形图)

index.js中：

```js
// 给series第一个对象里边添加yAxisIndex: 0
// 给series第二个对象里边添加yAxisIndex: 1
// 给series第一个对象里边
data: [70, 34, 60, 78, 69]
// 给series第二个对象里边
data: [100, 100, 100, 100, 100]
```

# 31-柱形图2定制7(带框的柱形图)

index.js中：

```js
// 给yAxis第一个对象里边添加inverse: true
// 给yAxis第二个对象里边添加inverse: true
// 记得给第二个柱状图添加自适应
```

# 32-折线图1引入到html页面中

index.js中：

```js
// 折线图1
option = {
    color: ['#00f2f1', '#ed3f35']
    tooltip: {
        trigger: 'axis'
    },
    legend: {
        // series如果写了name属性 这里不用写data
        right: '10%',
        textStyle: {
            color: '#4c9bfd'
        }
    },
    grid: {
        left: '3%',
        right: '4%',
        bottom: '3%',
        top: '20%',
        // 显示边框
        show: true,
        borderColor: '#012f4a',
        containLabel: true
    },
    xAxis: {
        type: 'category',
        boundaryGap: false,
        data: ['周一', '周二', '周三', '周四', '周五', '周六', '周日']，
        // 去除刻度线
        axisTick: {
        	show: false
    	},
    	// 文本颜色
    	axisLabel: {
            color: '#4c9bfd'
        },
    	// 去除轴线
    	axisLine: {
            show: false
        }
    },
    yAxis: {
        type: 'value'，
        // 去除刻度线
        axisTick: {
        	show: false
    	},
    	// 文本颜色
    	axisLabel: {
            color: '#4c9bfd'
        },
    	// 去除轴线
    	axisLine: {
            show: false
        }，
        // 分割线颜色
        splitLine: {
            lineStyle: {
                color: '#012f4a'
            }
        }
    },
    series: [
        {
            name: '邮件营销',
            type: 'line',
            smooth: true,
            data: [120, 132, 101, 134, 90, 230, 210]
        },
        {
            name: '联盟广告',
            type: 'line',
            smooth: true,
            data: [220, 182, 191, 234, 290, 330, 310]
        }
    ]
};
```

# 33-折线图1定制grid表格

# 34-折线图1定制x轴和y轴相关配置

# 35-折线图1定制俩条线的样式

# 36-折线图1数据更换

# 37-折线图1tab栏切换原理分析

index.html中：

```html
<h2>
    折线图-人员变化<a href="javascript:;">2020</a><a href="javascript:;">2021</a>
</h2>
```

index.less中：

```css
h2 {
    a {
        color: '#fff',
        text-decoration: none,
        margin: 0 10px;
    }
}
```

# 38-折线图1tab栏切换数据

添加jquery

index.js中：

```js
window.addEventListener();
$('.line h2').on('click', "a", function() {
    var obj = yearData[$(this).index()]
    option.series[0].data = obj.data[0]
    option.series[1].data = obj.data[1]
    myChart.setOption(option)
})
```

后台发送过来的数据：

```
var yearData = [
	{
		year: '2020',
		data:[
			[120, 132, 101, 134, 90, 230, 210],
			[250, 154, 101, 45, 98, 84, 210]
		]
	},
	{
		year: '2021',
		data:[
			[250, 154, 101, 45, 98, 84, 210],
			[120, 132, 101, 134, 90, 230, 210]
		]
	},
]
```

# 39-折线图2

index.js中：

```js
option = {
    tooltip: {
        trigger: 'axis',
    },
    legend: {
        top: '0%',
        data: ['邮件营销', '联盟广告', '视频广告', '直接访问', '搜索引擎'],
        textStyle: {
            color: "rgba(255, 255, 255, 0.5)",
            font-size: "12"
        }
    },
    grid: {
        left: '10',
        right: '10',
        bottom: '10',
        top: '30',
        containLabel: true
    },
    xAxis: [
        {
            type: 'category',
            boundaryGap: false,
            data: ['周一', '周二', '周三', '周四', '周五', '周六', '周日'],
            axisLabel: {
                textStyle: {
                    color: "rgba(255, 255, 255, 0.6)",
                    font-size: '12'
                }
            },
            axisLine: {
                lineStyle: {
                    color: 'rgba(255, 255, 255, 0.2)'
                }
            }
        }
    ],
    yAxis: [
        {
            type: 'value',
            axisTick: {
                show: false
            },
            axisLabel: {
                textStyle: {
                    color: "rgba(255, 255, 255, 0.6)",
                    font-size: '12'
                }
            },
            axisLine: {
                lineStyle: {
                    color: 'rgba(255, 255, 255, 0.1)'
                }
            },
            splitLine: {
                lineStyle: {
                    color: 'rgba(255, 255, 255, 0.1)'
                }
            }
        }
    ],
    series: [
        {
            name: '邮件营销',
            type: 'line',
            smooth: true,
            lineStyle: {
                color: '#0184d5'，
                width: '2'
            }
            areaStyle: {
                color: new echarts.graphic.LinearGradient(
            		0,0,0,1,
            		[
            			{offset: 0, color: 'rgba(1, 132, 213, 0.4)'},// 0% 处的颜色
        				{offset: 0.8, color: 'rgba(1, 132, 213, 0.1)'}
            		],
    				false
            	)
                shadowColor: "rgba(0, 0, 0, 0.1)"
        	},
            // 设置拐点为小圆点
            symbol: 'circle',
            symbolSize: 8,
            // 开始不显示拐点 鼠标经过时显示
            showSymbol: false,
            // 设置拐点的颜色和边框
            itemStyle: {
                color: "#0184d5",
                borderColor: 'rgba(221, 220, 107, 0.1)',
                borderWidth: 12
            },
            data: [120, 132, 101, 134, 90, 230, 210]
        },
        {
            name: '联盟广告',
            type: 'line',
            smooth: true,
            lineStyle: {
                normal: {
                    color: '#00d887'，
                    width: '2'
                }
            }
            areaStyle: {
                normal: {
                    color: new echarts.graphic.LinearGradient(
                        0,0,0,1,
                        [
                            {offset: 0, color: 'rgba(0, 216, 135, 0.4)'},// 0% 处的颜色
                            {offset: 0.8, color: 'rgba(0, 216, 135, 0.1)'}
                        ],
                        false
                    )
                }
                
                shadowColor: "rgba(0, 0, 0, 0.1)"
        	},
            // 设置拐点为小圆点
            symbol: 'circle',
            symbolSize: 8,
            // 开始不显示拐点 鼠标经过时显示
            showSymbol: false,
            // 设置拐点的颜色和边框
            itemStyle: {
                color: "#0184d5",
                borderColor: 'rgba(221, 220, 107, 0.1)',
                borderWidth: 12
            },
            data: [220, 182, 191, 234, 290, 330, 310]
        }
    ]
};
```

# 40-折线图2定制渐变填充区域

# 41-折线图2拐点配置

# 42-饼形图1

index.js中：

```js
option = {
    color: ['#065aab', '#066eab', '#0682ab', '#0696abb', '#06a0ab'],
    tooltip: {
        trigger: 'item',
        formatter: '{a} <br/>{b}: {c} ({d}%)'
    },
    legend: {
        bottom: '0%',
        itemWidth: 10,
        itemHeight: 10,
        textStyle: {
            color: "rgba(255, 255, 255, 0.5)",
            fontSizeL "12"
        }
    },
    series: [
        {
            name: '年龄分布',
            type: 'pie',
            // 设置饼形图在容器中的位置
            center: ['50%', '45%'],
            // 修改内圆半径和外圆半径
            radius: ['40%', '60%'],
            // 不显示标签文字
            label: {
                show: false，
                position: 'center'
            },
            // 不显示连接线
            labelLine: {
                show: false
            },
            avoidLabelOverlap: false,
            data: [
                {value: 1, name: '0岁以下'},
                {value: 4, name: '20-29岁'},
                {value: 2, name: '30-39岁'},
                {value: 2, name: '40-49岁'},
                {value: 1, name: '50岁以上'}
            ]
        }
    ]
};
```

柱形图-就业行业

折线图-人员变化

折线图-播放量

饼形图-年龄分布

# 43-饼形图2(南丁格尔玫瑰图)

index.js中：

```js
option = {
    color: ['#006cff', '#60cda0', '#ed8884', '#ff9f7f', '#0096ff', '#9fe6b8', '#32c5e9', '#1d9dff']
    tooltip: {
        trigger: 'item',
        formatter: '{a} <br/>{b} : {c} ({d}%)'
    },
    legend: {
        bottom: '0%',
        itemWidth: 10,
        itemHeight: 10,
        textStyle: {
            color: "rgba(255, 255, 255, 0.5)",
            fontSizeL "12"
        }
    },
    series: [
        {
            name: '地区分布',
            type: 'pie',
            radius: [10, 70],
            center: ['50%', '50%'],
            roseType: 'radius',
            // 图形的文字标签
            label: {
                fontSize: 10
            },
            labelLine: {
                length: 6,
                length2:8
            },
            data: [
                {value: 10, name: '云南'},
                {value: 5, name: '北京'},
                {value: 15, name: '山东'},
                {value: 25, name: '河北'},
                {value: 20, name: '江苏'},
                {value: 35, name: '浙江'},
                {value: 30, name: '四川'},
                {value: 40, name: '东北'}
            ]
        }
    ]
};
```

饼形图-地区分布

# 44-中国地图模拟飞行模块

模拟飞机航线：

https://gallery.echartsjs.com/editor.html?c=x0-ExSkZDM

下载并引入china.js文件（中国地图需要它）

index.js中：

```js
var geoCoordMap = {
    	    '上海': [121.4648,31.2891],
    	    '东莞': [113.8953,22.901],
    	    '东营': [118.7073,37.5513],
    	    '中山': [113.4229,22.478],
    	    '临汾': [111.4783,36.1615],
    	    '临沂': [118.3118,35.2936],
    	    '丹东': [124.541,40.4242],
    	    '丽水': [119.5642,28.1854],
    	    '乌鲁木齐': [87.9236,43.5883],
    	    '佛山': [112.8955,23.1097],
    	    '保定': [115.0488,39.0948],
    	    '兰州': [103.5901,36.3043],
    	    '包头': [110.3467,41.4899],
    	    '北京': [116.4551,40.2539],
    	    '北海': [109.314,21.6211],
    	    '南京': [118.8062,31.9208],
    	    '南宁': [108.479,23.1152],
    	    '南昌': [116.0046,28.6633],
    	    '南通': [121.1023,32.1625],
    	    '厦门': [118.1689,24.6478],
    	    '台州': [121.1353,28.6688],
    	    '合肥': [117.29,32.0581],
    	    '呼和浩特': [111.4124,40.4901],
    	    '咸阳': [108.4131,34.8706],
    	    '哈尔滨': [127.9688,45.368],
    	    '唐山': [118.4766,39.6826],
    	    '嘉兴': [120.9155,30.6354],
    	    '大同': [113.7854,39.8035],
    	    '大连': [122.2229,39.4409],
    	    '天津': [117.4219,39.4189],
    	    '太原': [112.3352,37.9413],
    	    '威海': [121.9482,37.1393],
    	    '宁波': [121.5967,29.6466],
    	    '宝鸡': [107.1826,34.3433],
    	    '宿迁': [118.5535,33.7775],
    	    '常州': [119.4543,31.5582],
    	    '广州': [113.5107,23.2196],
    	    '廊坊': [116.521,39.0509],
    	    '延安': [109.1052,36.4252],
    	    '张家口': [115.1477,40.8527],
    	    '徐州': [117.5208,34.3268],
    	    '德州': [116.6858,37.2107],
    	    '惠州': [114.6204,23.1647],
    	    '成都': [103.9526,30.7617],
    	    '扬州': [119.4653,32.8162],
    	    '承德': [117.5757,41.4075],
    	    '拉萨': [91.1865,30.1465],
    	    '无锡': [120.3442,31.5527],
    	    '日照': [119.2786,35.5023],
    	    '昆明': [102.9199,25.4663],
    	    '杭州': [119.5313,29.8773],
    	    '枣庄': [117.323,34.8926],
    	    '柳州': [109.3799,24.9774],
    	    '株洲': [113.5327,27.0319],
    	    '武汉': [114.3896,30.6628],
    	    '汕头': [117.1692,23.3405],
    	    '江门': [112.6318,22.1484],
    	    '沈阳': [123.1238,42.1216],
    	    '沧州': [116.8286,38.2104],
    	    '河源': [114.917,23.9722],
    	    '泉州': [118.3228,25.1147],
    	    '泰安': [117.0264,36.0516],
    	    '泰州': [120.0586,32.5525],
    	    '济南': [117.1582,36.8701],
    	    '济宁': [116.8286,35.3375],
    	    '海口': [110.3893,19.8516],
    	    '淄博': [118.0371,36.6064],
    	    '淮安': [118.927,33.4039],
    	    '深圳': [114.5435,22.5439],
    	    '清远': [112.9175,24.3292],
    	    '温州': [120.498,27.8119],
    	    '渭南': [109.7864,35.0299],
    	    '湖州': [119.8608,30.7782],
    	    '湘潭': [112.5439,27.7075],
    	    '滨州': [117.8174,37.4963],
    	    '潍坊': [119.0918,36.524],
    	    '烟台': [120.7397,37.5128],
    	    '玉溪': [101.9312,23.8898],
    	    '珠海': [113.7305,22.1155],
    	    '盐城': [120.2234,33.5577],
    	    '盘锦': [121.9482,41.0449],
    	    '石家庄': [114.4995,38.1006],
    	    '福州': [119.4543,25.9222],
    	    '秦皇岛': [119.2126,40.0232],
    	    '绍兴': [120.564,29.7565],
    	    '聊城': [115.9167,36.4032],
    	    '肇庆': [112.1265,23.5822],
    	    '舟山': [122.2559,30.2234],
    	    '苏州': [120.6519,31.3989],
    	    '莱芜': [117.6526,36.2714],
    	    '菏泽': [115.6201,35.2057],
    	    '营口': [122.4316,40.4297],
    	    '葫芦岛': [120.1575,40.578],
    	    '衡水': [115.8838,37.7161],
    	    '衢州': [118.6853,28.8666],
    	    '西宁': [101.4038,36.8207],
    	    '西安': [109.1162,34.2004],
    	    '贵阳': [106.6992,26.7682],
    	    '连云港': [119.1248,34.552],
    	    '邢台': [114.8071,37.2821],
    	    '邯郸': [114.4775,36.535],
    	    '郑州': [113.4668,34.6234],
    	    '鄂尔多斯': [108.9734,39.2487],
    	    '重庆': [107.7539,30.1904],
    	    '金华': [120.0037,29.1028],
    	    '铜川': [109.0393,35.1947],
    	    '银川': [106.3586,38.1775],
    	    '镇江': [119.4763,31.9702],
    	    '长春': [125.8154,44.2584],
    	    '长沙': [113.0823,28.2568],
    	    '长治': [112.8625,36.4746],
    	    '阳泉': [113.4778,38.0951],
    	    '青岛': [120.4651,36.3373],
    	    '韶关': [113.7964,24.7028]
    	};

    	var XAData = [
    	    [{name:'西安'}, {name:'北京',value:100}],
    	    [{name:'西安'}, {name:'上海',value:100}],
    	    [{name:'西安'}, {name:'广州',value:100}],
    	    [{name:'西安'}, {name:'西宁',value:100}],
    	    [{name:'西安'}, {name:'银川',value:100}]
    	];

    	var XNData = [
    	    [{name:'西宁'}, {name:'北京',value:100}],
    	    [{name:'西宁'}, {name:'上海',value:100}],
    	    [{name:'西宁'}, {name:'广州',value:100}],
    	    [{name:'西宁'}, {name:'西安',value:100}],
    	    [{name:'西宁'}, {name:'银川',value:100}]
    	];

    	var YCData = [
    	    [{name:'银川'}, {name:'北京',value:100}],
    	    [{name:'银川'}, {name:'广州',value:100}],
    	    [{name:'银川'}, {name:'上海',value:100}],
    	    [{name:'银川'}, {name:'西安',value:100}],
    	    [{name:'银川'}, {name:'西宁',value:100}],
    	];

    	var planePath = 'path://M1705.06,1318.313v-89.254l-319.9-221.799l0.073-208.063c0.521-84.662-26.629-121.796-63.961-121.491c-37.332-0.305-64.482,36.829-63.961,121.491l0.073,208.063l-319.9,221.799v89.254l330.343-157.288l12.238,241.308l-134.449,92.931l0.531,42.034l175.125-42.917l175.125,42.917l0.531-42.034l-134.449-92.931l12.238-241.308L1705.06,1318.313z';
    	//var planePath = 'arrow';
    	var convertData = function (data) {
    			
    	    var res = [];
    	    for (var i = 0; i < data.length; i++) {
    	    	
    	        var dataItem = data[i];

    	        var fromCoord = geoCoordMap[dataItem[0].name];
    	        var toCoord = geoCoordMap[dataItem[1].name];
    	        if (fromCoord && toCoord) {
    	            res.push({
    	                fromName: dataItem[0].name,
    	                toName: dataItem[1].name,
    	                coords: [fromCoord, toCoord],
    	                value: dataItem[1].value
    	            });
    	        }
    	    }
    	    return res;
    	   	
    	};

    	var color = ['#a6c84c', '#ffa022', '#46bee9'];//航线的颜色
    	var series = [];
    	[['西安', XAData], ['西宁', XNData], ['银川', YCData]].forEach(function (item, i) {  
    	    series.push({
    	        name: item[0] + ' Top3',
    	        type: 'lines',
    	        zlevel: 1,
    	        effect: {
    	            show: true,
    	            period: 6,
    	            trailLength: 0.7,
    	            color: 'red',   //arrow箭头的颜色
    	            symbolSize: 3
    	        },
    	        lineStyle: {
    	            normal: {
    	                color: color[i],
    	                width: 0,
    	                curveness: 0.2
    	            }
    	        },
    	        data: convertData(item[1])
    	    },
    	    {
    	        name: item[0] + ' Top3',
    	        type: 'lines',
    	        zlevel: 2,
    	        symbol: ['none', 'arrow'],
    	        symbolSize: 10,
    	        effect: {
    	            show: true,
    	            period: 6,
    	            trailLength: 0,
    	            symbol: planePath,
    	            symbolSize: 15
    	        },
    	        lineStyle: {
    	            normal: {
    	                color: color[i],
    	                width: 1,
    	                opacity: 0.6,
    	                curveness: 0.2
    	            }
    	        },
    	        data: convertData(item[1])
    	    },
    	    {
    	        name: item[0] + ' Top3',
    	        type: 'effectScatter',
    	        coordinateSystem: 'geo',
    	        zlevel: 2,
    	        rippleEffect: {
    	            brushType: 'stroke'
    	        },
    	        label: {
    	            normal: {
    	                show: true,
    	                position: 'right',
    	                formatter: '{b}'
    	            }
    	        },
    	        symbolSize: function (val) {
    	            return val[2] / 8;
    	        },
    	        itemStyle: {
    	        	normal: {
    	        		color: color[i],
		            },
		            emphasis: {
		                areaColor: '#2B91B7'
		            }
    	        },
    	        data: item[1].map(function (dataItem) {
    	            return {
    	                name: dataItem[1].name,
    	                value: geoCoordMap[dataItem[1].name].concat([dataItem[1].value])
    	            };
    	        })
    	    });
    	});
    	var option = {
    	    tooltip : {
    	        trigger: 'item', 
    	        formatter:function(params, ticket, callback){
    	            if(params.seriesType=="effectScatter") {
    	                return "线路："+params.data.name+""+params.data.value[2];
    	            }else if(params.seriesType=="lines"){
    	                return params.data.fromName+">"+params.data.toName+"<br />"+params.data.value;
    	            }else{
    	                return params.name;
    	            }
    	        } 
    	    },
    	    legend: {
    	        orient: 'vertical',
    	        top: 'bottom',
    	        left: 'right',
    	        data:['西安 Top3', '西宁 Top3', '银川 Top3'],
    	        textStyle: {
    	            color: '#fff'
    	        },
    	        selectedMode: 'multiple'
    	    },
    	    geo: {
    	        map: 'china',
                // 把地图放大1.2倍
                zoom: 1.2,
    	        label: {
    	            emphasis: {
    	                show: true,
    	                color:'#fff'
    	            }
    	        },
    	        roam: true,
    	        itemStyle: {
    	        	normal: {
                        // 地图省份的背景颜色
		                areaColor: 'rgba(20, 41, 87, 0.6)',
		                borderColor: '#0692a4',
		                borderWidth: 1,
		            },
		            emphasis: {
		                areaColor: '#0b1c2d'
		            }
    	        }
    	    },
    	    series: series
    	};
```

# 45-约束屏幕尺寸

index.css中：

```css
.column:nth-child(2) {
    /* 图片旋转的时候把图片多余的部分截掉 这样底部不会有一部分白的 */ 
    overflow: hidden
}
/* 放在该文件的最后 */
/* 约束屏幕尺寸 */
/* 屏幕宽度比1024小 设置文字大小为42px不变 */
@media screen and (max-width: 1024px) {
    html {
        font-size: 42px !important;
    }
}
/* 屏幕宽度比1920大 设置文字大小为80px不变 */
@media screen and (min-width: 1920px) {
    html {
        font-size: 80px !important;
    }
}

```









