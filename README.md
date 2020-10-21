# Leaflet.ShowHideLayerGroup
leaflet中如何通过透明度控制layerGroup的显示隐藏。

## 简介：

最近翻看leaflet的API文档，发现leaflet中没有直接控制LayerGroup显示隐藏的方法，那如何来实现LayerGroup的显示和隐藏呢？

通常有如下两种思路：

第一种，隐藏时清除图层，显示时重新添加图层，当数据量较小，并且不需要频繁切换图层显示隐藏时，使用这种方式较为方便。但是，当数据量较大，或需要频繁切换图层显示隐藏时，使用这种方式则会增加对浏览器的压力，出现卡顿现象。

第二种，遍历图层内部所有要素，通过控制要素透明度的方式，达到控制图层显示隐藏的目的。此方式可以解决在数据量较大，或需要频繁切换图层显示隐藏时，出现卡顿的情况。

我们将第二种方式封装成插件，而且支持`maker`要素 和 `vector`要素同时控制，还记录了要素默认状态下的透明度，以保证切换到显示时与原样式一致，方便大家使用。

## 用法：

在html文件中，引入 Leaflet.ShowHideLayerGroup.js 插件，调用`showLayer()`、`hideLayer()`方法就能实现对layergroup显示隐藏控制。

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

