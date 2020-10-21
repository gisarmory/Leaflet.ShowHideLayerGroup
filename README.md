# Leaflet.ShowHideLayerGroup
Leaflet通过LayerGroup控制大量、多种图层显示隐藏。

## 简介：

在使用leaflet进行点、线、面等图层管理时，经常会遇到对图层显示隐藏控制的需求，对于单个图层好说，只需要对图层样式重新编辑即可。但是当遇到需要对大量、多种图层同时控制时，再逐个图层编辑样式就有些繁琐了，这时候就用到了L.LayerGroup()。如何通过LayerGroup来控制多个图层的显示隐藏呢，通常有如下两种思路：

第一种，隐藏时清除图层，显示时重新添加图层，当数据量较小而且不需要频繁切换图层显示隐藏时，使用这种方式较为方便；但是，当数据量较大或者需要频繁切换图层显示隐藏时，使用这种方式则会增加对浏览器的压力，出现卡顿现象。

第二种，通过‘layergroup.eachLayer()’方法循环遍历控制图层显示隐藏，此方式通过修改图层样式直接控制图层显示隐藏，在数据量较大或者需要频繁切换显示隐藏时，都比较流畅。

我们将第二种方式封装成Leaflet.ShowHideLayerGroup.js插件，而且支持maker图层 和 vector图层同时控制，还记录了图层默认状态下的透明度，以保证切换到显示时与原样式一致，方便大家使用。

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

