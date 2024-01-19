## 什么是bfc
是一个独立的渲染区域，并且与这个区域外部毫不相干，也就是一个独立的盒子的概念，他不会影响外部元素的布局。

## 显著特性呢？
#### 相邻兄弟元素的marin-bottom和margin-top的值发生重叠
请看示例：![示例](https://codesandbox.io/p/sandbox/competent-hermann-v5klst?file=%2Findex.html%3A23%2C11&layout=%257B%2522sidebarPanel%2522%253A%2522EXPLORER%2522%252C%2522rootPanelGroup%2522%253A%257B%2522direction%2522%253A%2522horizontal%2522%252C%2522contentType%2522%253A%2522UNKNOWN%2522%252C%2522type%2522%253A%2522PANEL_GROUP%2522%252C%2522id%2522%253A%2522ROOT_LAYOUT%2522%252C%2522panels%2522%253A%255B%257B%2522type%2522%253A%2522PANEL_GROUP%2522%252C%2522contentType%2522%253A%2522UNKNOWN%2522%252C%2522direction%2522%253A%2522vertical%2522%252C%2522id%2522%253A%2522clrh6vv9g00063b6kymf4kfke%2522%252C%2522sizes%2522%253A%255B100%252C0%255D%252C%2522panels%2522%253A%255B%257B%2522type%2522%253A%2522PANEL_GROUP%2522%252C%2522contentType%2522%253A%2522EDITOR%2522%252C%2522direction%2522%253A%2522horizontal%2522%252C%2522id%2522%253A%2522EDITOR%2522%252C%2522panels%2522%253A%255B%257B%2522type%2522%253A%2522PANEL%2522%252C%2522contentType%2522%253A%2522EDITOR%2522%252C%2522id%2522%253A%2522clrh6vv9f00023b6kigxnh3dg%2522%257D%255D%257D%252C%257B%2522type%2522%253A%2522PANEL_GROUP%2522%252C%2522contentType%2522%253A%2522SHELLS%2522%252C%2522direction%2522%253A%2522horizontal%2522%252C%2522id%2522%253A%2522SHELLS%2522%252C%2522panels%2522%253A%255B%257B%2522type%2522%253A%2522PANEL%2522%252C%2522contentType%2522%253A%2522SHELLS%2522%252C%2522id%2522%253A%2522clrh6vv9g00033b6kstnc5lc7%2522%257D%255D%252C%2522sizes%2522%253A%255B100%255D%257D%255D%257D%252C%257B%2522type%2522%253A%2522PANEL_GROUP%2522%252C%2522contentType%2522%253A%2522DEVTOOLS%2522%252C%2522direction%2522%253A%2522vertical%2522%252C%2522id%2522%253A%2522DEVTOOLS%2522%252C%2522panels%2522%253A%255B%257B%2522type%2522%253A%2522PANEL%2522%252C%2522contentType%2522%253A%2522DEVTOOLS%2522%252C%2522id%2522%253A%2522clrh6vv9g00053b6ktwau65h1%2522%257D%255D%252C%2522sizes%2522%253A%255B100%255D%257D%255D%252C%2522sizes%2522%253A%255B50%252C50%255D%257D%252C%2522tabbedPanels%2522%253A%257B%2522clrh6vv9f00023b6kigxnh3dg%2522%253A%257B%2522tabs%2522%253A%255B%257B%2522id%2522%253A%2522clrh6vv9e00013b6kcdtf5zl8%2522%252C%2522mode%2522%253A%2522permanent%2522%252C%2522type%2522%253A%2522FILE%2522%252C%2522filepath%2522%253A%2522%252Findex.html%2522%252C%2522state%2522%253A%2522IDLE%2522%252C%2522initialSelections%2522%253A%255B%257B%2522startLineNumber%2522%253A23%252C%2522startColumn%2522%253A11%252C%2522endLineNumber%2522%253A23%252C%2522endColumn%2522%253A11%257D%255D%257D%255D%252C%2522id%2522%253A%2522clrh6vv9f00023b6kigxnh3dg%2522%252C%2522activeTabId%2522%253A%2522clrh6vv9e00013b6kcdtf5zl8%2522%257D%252C%2522clrh6vv9g00053b6ktwau65h1%2522%253A%257B%2522tabs%2522%253A%255B%257B%2522id%2522%253A%2522clrh6vv9g00043b6krgtvxgtb%2522%252C%2522mode%2522%253A%2522permanent%2522%252C%2522type%2522%253A%2522UNASSIGNED_PORT%2522%252C%2522port%2522%253A0%252C%2522path%2522%253A%2522%252F%2522%257D%255D%252C%2522id%2522%253A%2522clrh6vv9g00053b6ktwau65h1%2522%252C%2522activeTabId%2522%253A%2522clrh6vv9g00043b6krgtvxgtb%2522%257D%252C%2522clrh6vv9g00033b6kstnc5lc7%2522%253A%257B%2522tabs%2522%253A%255B%255D%252C%2522id%2522%253A%2522clrh6vv9g00033b6kstnc5lc7%2522%257D%257D%252C%2522showDevtools%2522%253Atrue%252C%2522showShells%2522%253Afalse%252C%2522showSidebar%2522%253Atrue%252C%2522sidebarPanelSize%2522%253A15%257D) 
属于同一个BFC的，他们的上下margin会重叠，注意是上下margin，左右不存在折叠
![image](https://github.com/zenglincient/Front-End-Development-Notes/assets/18399043/461bcb10-4222-45af-b07d-9d5f6e732263)

但是，此时如果把他们置于不同的bfc，那么margin就不会重叠了

![image](https://github.com/zenglincient/Front-End-Development-Notes/assets/18399043/64a319e7-82d5-40a2-8074-8c387768cf4c)

可见，同一个bfc会发生margin折叠。

#### 父级和第一个/最后一个子元素的margin合并
同一个bfc中，上下，父子重叠在一起了！
![image](https://github.com/zenglincient/Front-End-Development-Notes/assets/18399043/a34ddefe-29fa-4b48-a8bc-707c88755a86)
此刻，如果我加了一个让wrapper变成bfc的魔法
![image](https://github.com/zenglincient/Front-End-Development-Notes/assets/18399043/aa8d8c9f-bfb8-47fc-a94e-5c6605482976)

合并规则
a、全部都为正值，取最大者
b、不全是正值，则都取绝对值，然后用正值减去最大值；
c、没有正值，则都取绝对值，然后用0减去最大值。

#### 浮动清除
什么是浮动
正常盒子的领地被侵犯+高度塌陷
![image](https://github.com/zenglincient/Front-End-Development-Notes/assets/18399043/9c6bdc55-4a22-4ff0-abb9-1367401678d0)
这里还有一个小细节，哪怕领地被侵犯，文本也不会被遮挡！因为文本就设计成要环绕float元素的，不会被侵犯领地。这可能是和古老的html中浮动文字在图片周围有关。
此时施展魔法变成bfc
![image](https://github.com/zenglincient/Front-End-Development-Notes/assets/18399043/9112d1c1-5dc7-4d52-8039-faa625c26edc)

此刻可以看到，高度塌陷解决了，领地侵犯怎么办？
此时，再次施展魔法，把正常的蓝色盒子变成bfc
![image](https://github.com/zenglincient/Front-End-Development-Notes/assets/18399043/55c55e6c-cd06-4d7d-a739-15a906d75c06)

## 如何触发bfc魔法
【1】根元素，即HTML元素
【2】float的值不为none
【3】overflow的值不为visible
【4】display的值为inline-block、table-cell、table-caption
【5】position的值为absolute或fixed

## BFC魔法的使用场景
#### 三栏布局
如图
![image](https://github.com/zenglincient/Front-End-Development-Notes/assets/18399043/cb75d737-5bec-4898-9383-bbee5df50035)

```
<!DOCTYPE html>
<html charset="utf-8">
  <head>
    <style>
      .container {
        border: 2px solid black;
        padding: 10px;
      }

      .float-box {
        float: left;
        width: 100px;
        height: 300px;
        background-color: red;
        margin-right: 10px;
      }

      .float-box-right {
        float: right;
        width: 100px;
        height: 300px;
        background-color: red;
        margin-left: 10px;
      }

      .normal-box {
        height: 300px;
        margin-left: 100px;
        margin-right: 100px;
        background-color: blue;
        overflow: hidden;
      }
    </style>
  </head>
  <body>
    <div class="container">
      <div class="float-box">
        浮动盒子浮动盒子浮动盒子浮动盒子浮动盒子浮动盒子浮动盒子浮动盒子浮动盒子浮动盒子浮动盒子
      </div>

      <div class="float-box-right">
        浮动盒子浮动盒子浮动盒子浮动盒子浮动盒子浮动盒子浮动盒子浮动盒子浮动盒子浮动盒子浮动盒子
      </div>
      <div class="normal-box">
        1111普通盒子普通盒子普通盒子普通盒子普通盒子普通盒子普通盒子普通盒子普通盒子普通盒子普通盒子
      </div>
    </div>
  </body>
</html>

```
