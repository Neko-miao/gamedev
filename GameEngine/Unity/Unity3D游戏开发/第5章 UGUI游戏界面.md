# UGUI游戏界面
## 1. 基础元素
- Text
- 描边和阴影  
    - 描边会在原Text字体上、下、左、右各画一遍，效率低；阴影只需多画一遍
- 动态字体  
    - 动态字体根据传入的字体和字体大小生成一张纹理图，最终将纹理上的字体显示出来。缺点在于，会生成多份纹理图。  
    - 可以使用**SDF**字体，它的原理是利用位图来保存矢量信息，记录到边的最短距离，最后再用shader还原回来。推荐*TextMeshPro*插件  
- 字体花屏  
    - 动态字体会动态生成材质，当问题太多时，会触发UGUI内部重建字体贴图命令，就可能造成文字花屏。  
    - 可以监听`Font.textureRebuilt`事件，并在`Update()`中调用`FontTextureChanged()`方法，刷新所有Text文本
- Image组件  
    - simple：直接显示
    - Sliced：九空格显示，可用SpriteEditor编辑
    - Tiled：平铺图片
    - Filled：像技能cd一样，可以旋转图片  
- Raw Image组件  
    - Image只能显示Sprite，Raw Image可以显示任意Texture，也可以显示Sprite。
    - Image可以用Atlas来合并批次，Raw Image不能，它只占一次DrawCall，不太建议使用。
    - 使用Raw Imgae：如Render Texture，需要将摄像机渲染到纹理中。

- Button组件  
    - 必须依赖Image，有普通、点击、抬起和悬浮状态
    - `onClick.AddListener()`添加监听事件

- Toggle组件
    - 单项选择，选择其中一个，其他的会自动取消，需要将Toggle对象关联到同一个ToggleGroup中
    - `onValueChanged()`方法监听切换事件

- Slider组件  
    - 游戏中常用来坐人物的血条
    - `onValueChanged()`方法监听Slider组件的滚动事件，可以取到滚动条进度

- Scrollbar & ScrollView组件
    - Scroll Rect组件由Scrollbar（拖动条）和ScrollView（滑动区域）组成

- 使用ScrollRect组件制作游戏摇杆

## 2. 事件系统
UGUI所有的事件都是依赖EeventSsystem组件完成

### 2.1 UI事件
- UI事件依赖于Graphic Raycast组件，它必须绑定在Canvas组件上
- UGUI事件监听方法：
    - `OnPointerEnter`:进入该区域时调用
    - `OnPointerExit`:离开该区域时调用
    - `OnPointerDown`:按下时调用
    - `OnPointerUp`:抬起时调用
    - `OnPointerClick`
    - `OnInitializedPotentialDrag`：拖动初始化
    - `OnbeginDrag`：拖动开始时调用，且可取到拖动方向
    - `OnDrag`:滑动持续时调用
    - `OnEndDrag`：拖动结束时调用
    - `OnDrop`：落下时调用
    - `OnScroll`：鼠标滚轮持续时调用
    - `OnUpdateSelected`:选择时持续调用，只针对Selectable
    - `OnSelect`：选择后调用，只针对Selectable
    - `OnDeselect`：取消选择，注意Selectable只能选择一个
    - `OnMove`:监听上下左右WSAD方向键，eventData.moveDir表示方向
    - `OnSubmit`:按钮按下事件
    - `OnCancel`:按钮取消事件，按下时按Esc可取消
