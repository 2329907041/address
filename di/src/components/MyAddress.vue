<script setup>
import AMapLoader from '@amap/amap-jsapi-loader';
import { onMounted } from 'vue'



onMounted(() => {
  const marker = new AMap.Marker({
    position: [116.39, 39.9] //位置
})
map.add(marker); //添加到地图
  const lineArr = [
  [116.368904, 39.913423],
  [116.382122, 39.901176],
  [116.387271, 39.912501],
  [116.398258, 39.904600]
];
const polyline = new AMap.Polyline({
  path: lineArr,          // 设置线覆盖物路径
  strokeColor: "#3366FF", // 线颜色
  strokeWeight: 5,        // 线宽
  strokeStyle: "solid",   // 线样式
});
map.add(polyline);

// 创建信息窗体
const infoWindow = new AMap.InfoWindow({ 
  isCustom: true,  // 使用自定义窗体
  content: '<div>HELLO,AMAP!</div>', // 信息窗体的内容可以是任意 html 片段
  offset: new AMap.Pixel(16, -45)
});
const onMarkerClick = function(e) {
  infoWindow.open(map, e.target.getPosition()); // 打开信息窗体
  // e.target 就是被点击的 Marker
} 

    window._AMapSecurityConfig = {
        securityJsCode: '30dd606ff3e01b8fd32a10b34dd1a61b',
    },
        AMapLoader.load({
            "key": "256a4731188bc669d5e3c5f8c42c5b7e",              // 申请好的Web端开发者Key，首次调用 load 时必填
            "version": "2.0",   // 指定要加载的 JS API 的版本，缺省时默认为 1.4.15
            "plugins": [],           // 需要使用的的插件列表，如比例尺'AMap.Scale'等
        }).then((AMap) => {
            map = new AMap.Map('container');
        }).catch(e => {
            console.log(e);
        })
}),
</script>


<template>
    <div id="container"></div>
</template>

 
<style>
div{
  height: 50%;
  width: 50%;
}
</style>