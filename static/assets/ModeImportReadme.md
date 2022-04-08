## 模型文件导入方法

### 模型提供规范（模型组）
1. 提供FBX+PNG格式模型文件，命名一致，以米为单位输出，Z轴向上，扩展名均为小写，例如BusStop.fbx\BusStop.png
2. 提供jpg格式预览图片文件，命名与fbx命名一致，例如BusStop.jpg
3. 提供描述文件列表，例如 BusStop
4. 模型提供的UV文件必须要在框内，不能出框
5. 可选，如果由多个模型组成，例如：BusStop_0.fbx\BusStop_1.fbx + BusStop_0.png\BusStop_1.png，描述文件增加multiFile:2,文件个数
6. 可选，如果无法提供fbx，必须提供obj+mtl格式，命名保持一致，规律和上方一样，mtl关联的贴图文件采用同级目录关联，描述文件增加obj:true
---
参考描述文件如下
```yaml
- CoconutTree:
  multiFile: 2
- BusStop:
  obj: true
```

### 模型导入规范（编辑器）
1. 模型文件采用yml格式导入，分为static/assets/tree.yml文件和src/common/lang/en.js & zh.js 翻译文件
2. yml格式采用以下结构， 均为数组描述，前三级为分类，从第四级开始是具体模型描述，第四级可以是组也可以是对象形式，组的形式代表多个模型合并成一个，对象代表一个模型，
   每个对象命名规范要求提供的模型、贴图、展示文件均要求与第四级的名称一样，模型描述具有以下属性
- model： 模型文件名称, 可选， 默认为上级名称
- mapping: 贴图文件名称, 可选， 默认为上级名称
- multiFile:分文件数量, 可选， 默认为1个，针对多个模型组合的情况，模型和贴图需要采用标准规范命名，缩略图要求jpg格式，例如以下CoconutTree由两个文件组成分别为CoconutTree_1.fbx\CoconutTree_2.fbx文件
- scale：缩放比，, 可选， 默认为1，下例中提供的模型将以0.01缩放比展示在场景中，米级单位
- obj：当前提供的文件是否是obj\mtl + png 文件，否则是fbx+png文件, 可选， 默认为fbx格式
- rotateX: 模型沿X轴逆时针旋转角度, 可选， 默认为0
- rotateY: 模型沿Y轴逆时针旋转角度, 可选， 默认为0
- rotateZ: 模型沿Z轴逆时针旋转角度, 可选， 默认为0
- offsetX: 模型沿X轴偏移长度, 可选， 默认为0
- offsetY: 模型沿X轴偏移长度, 可选， 默认为0
- offsetZ: 模型沿X轴偏移长度, 可选， 默认为0
---
例如以下例子提供的模型文件为：
CoconutTree_0.obj\CoconutTree_0.mtl\CoconutTree_1.obj\CoconutTree_1.mtl\CoconutTree.png\CoconutTree.jpg
```yaml
Model:
  - StonePlants:
    - Trees:
      - CoconutTree:
          multiFile: 2
          scale: 0.01
          model: yuan
          mapping: width_limit_3_5
          obj: true
      - Pine:
        - model: yuan
          scale: 0.01
          mapping: width_limit_3_5
          obj: true
        - model: ganzi
          scale: 0.01
          mapping: width_limit_3_5
          obj: true
```