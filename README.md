1.下载最新的功能代码，路径https://gcode.uniview.com/rd-sw1/rd-sw-t3/rd-sw-ue5/UE5.git，复制lContent下所有文件到需要打包项目content文件夹下
2.设置默认关卡========打开项目设置-地图和模式，设置游戏默认地图为当前编辑器关卡
3.启用插件===========打开插件界面，启用如下插件：Json Blueprint Utilities、Cesium for Unreal、Pixel Streaming，重启编辑器
4.设置控制模式=======打开窗口-世界场景设置，设置游戏模式，选择mode
5.设置楼层拉开=======找到functions/scene/floorControl，拖入到需要拉开的楼层下面，和楼层平级，注意楼层必须按照规范命名且位于actor下，打包前点击初始化
6.设置灯光功能=======打开functions/utils/light文件，找到函数TurnOn-获取有接口的所有actor，将interface设置为灯光开关的接口lightInterface
7.设置后期处理盒子===面板里找到PostProcessVolume-后期处理材质，增加一个材质，选择M_OutLine_Inst，继续找到后期处理体积设置，找到无限范围，勾上
8.如果动态天空使用的不是根目录，需要替换
9.生成场景json文件===找到functions/scene/scene_json，拖入到场景，运行项目，按 Ctrl+O 会在项目根目录生成json文件
10.创建建筑actor(datasmithsceneactor)，将所有楼层置于建筑actor下，为每一个楼层实例添加tag(floor:1)
11.添加内置点位 将模型加入合适位置，为其添加tag(layerName:dmsxt、name:dmsxt3)
12.生成楼层json文件 将sceneInit拖到场景中（若场景中存在可以直接选用），点击生成json后生成文件到项目根目录
13.添加内置点位设备进入场景：导入datasmith资产，删除点位模型中自带的楼层模型（通常在末尾），将场景中的楼层模型位置修改到点位模型父级元素，选择所有相机设置可视域材质，添加标签layerName:SXT_2F、name:SXT，修改后将此楼层下的所有相机移动到对应楼层下
14.道路上车模型引自AssetsLibrary/BluePrint/Spline/Move/Spline_CarFlow
15.批量修改楼层下的tag，sceneInit中先设置Model Name Start中索引为设备名的前缀，点击设置设备tag值
16.当前建筑虚化时需要遍历楼层设置碰撞set collision enable为无碰撞
end.打开平台-Windows，打包项目