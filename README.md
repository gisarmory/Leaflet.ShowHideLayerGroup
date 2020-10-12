# Leaflet.ShowHideLayerGroup
Leaflet LayerGroup 图层组显示隐藏插件。

## 简介：

使用leaflet添加点、线、面等图层时，添加到L.layerGroup()中，可方便同层统一管理，在控制图层显示隐藏时，有两种思路：
第一种，通常处理方式是清除后添加图层，这种方式会增加对浏览器的压力，且数据量较大时会有卡顿现象，不可取。
第二种，通过‘layergroup.eachLayer()’方法循环遍历控制图层显示隐藏，此方式通过对图层样式直接控制显示隐藏，效果较好（由于maker图层 和 vector图层样式控制方式不同，需放在两个图层组来控制）。

我们将第二种方式封装成Leaflet.ShowHideLayerGroup.js插件，方便大家使用。

## 用法：

在html文件中，引入Leaflet.ShowHideLayerGroup.js插件，调用“showLayer()”、“hideLayer()”就能实现对layergroup显示隐藏控制。

## 示例：

~~~ html
    <!-- 引入leafletapi -->
    <link rel="stylesheet" href="./lib/leaflet.css" />
    <script src="./lib/leaflet.js"></script>

    <!-- 引入图层组显示隐藏插件 -->
    <script type="text/javascript" src='../dist/leaflet.ShowHideLayerGroup.min.js'></script>
~~~

~~~ js
	// 初始化地图
    var map = L.map('map', {
        center: [39.905963, 116.320813],
        zoom: 12,
        preferCanvas: true //使用canvas模式渲染矢量图形 
    });
    // 添加底图
    var tiles = L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png').addTo(map);

	//初始化layergroup
	var myLayerGroup = L.layerGroup().addTo(map)

    // 图层显示
    function showLayer() {
        myLayerGroup.showLayer()
    }

    // 图层隐藏
    function hideLayer() {
        myLayerGroup.hideLayer()
    }
~~~

下面是在线示例：

[在线示例](http://gisarmory.xyz/Leaflet.ShowHideLayerGroup/examples/index.html)



## 君子协议
只要star本库，并关注公众号“GIS兵器库”，你就可以免费使用此插件。公众号二维码：

![](http://blogimage.gisarmory.xyz/20200923063756.png)

（若上方二维码无法显示，点此链接 [GIS兵器库](http://blogimage.gisarmory.xyz/20200923063756.png) ）

## 相关链接

[Leaflet](https://leafletjs.com/index.html)

## 免责声明

该插件中集成的纠偏算法，是基于网络上公开已知的，其他语言算法实现的移植版本，作者不对其准确性和合法性做保证。**请在遵守国家保密法的前提下自行斟酌使用**。