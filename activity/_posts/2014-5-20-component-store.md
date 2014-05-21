---
layout: post
title: 收藏
authors:
  - name: 宫晴
---

---

## 简介

收藏接口用于收藏店铺。一个品牌可能有多个店铺。如果在APP自定义接口里对该品牌配置了多个店铺ID，则收藏时会收藏所有已配置的店铺；检测是否收藏时，只要有一个店铺没有收藏，则返回未收藏。

## 模块引用

```javascript
/**** 天猫 *****/
KISSY.use("mmcomponents/mamaStore/index",function(S,mmStore){})
```

## 接口
该组件返回一个构造函数，若要调用需先创建一个新的对象

### 初始化
初始化一个收藏模块

+ 用法

```javascript
var mStore = new mmStore({
  app: "chowsangsang"
});
```

+ 参数

对象字面量类型

|  name      |  type    |  introduction  |
| -----------| -------  |--------------- |
|  app       |  String  |必填。活动app名称，在自定义接口中设置 |

### checkStore
检测是否收藏店铺。如上所说，只要有一个店铺没有收藏，则返回未收藏。两个参数都是可选的。

+ 用法

```javascript
mStore.checkStore({
  have: function(){},
  no  : function(){}
})
```

+ 参数

对象字面量类型

|  name      |  type    |  introduction  |
| -----------| -------  |--------------- |
|  have      | Function |如果已经收藏则执行此回调 |    
|  no        | Function |如果未收藏则执行此回调   |


### store
收藏店铺。如上所说，收藏时会收藏所有已配置的店铺。

+ 用法

```javascript
mStore.store(function(){})
```

### 示例

```javascript
var mStore = new mmStore({
  app: "gongqing"
});

mStore.checkStore({
  have: function(){
  	alert("您已经收藏啦！");
  },
  no  : function(){
  	mStore.store(function(){
  	  alert("收藏成功！");
    })
  }
})
```


+ 参数

只有一个参数，为收藏成功后执行的回调函数。若收藏失败，会alert收藏失败的弹窗。可为空。

## Demo
[收藏](http://www.taobao.com/market/alimama/store.php)