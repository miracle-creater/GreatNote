### v-cloak

先通过隐藏样式在内存中进行值的替换，替换好之后再替换最终的结果

```js
//1. style样式中添加
[v-cloak]{display: none;}
//2.
<div id="pay" v-cloak>
    {{boxer}}
<div/>
```

### v-text

填充纯文本（不存在闪动问题）

### v-html

作用：填充HTML片段

- 容易导致XSS攻击，永不用在用户提交的内容上

- 本网站的内容可以使用，来自于第三方的数据不能使用

### v-pre  

按照原始信息进行填充，vue不对信息进行处理（跳过编译过程） 

### v-once 

只编译一次

- 显示内容之后不具有响应式的功能（只能进行一次改动）

### v-model

> - 使用v-model
>   - 实现数据的监听（用在form表单，数据输入框）
> - 修饰符
>   - `v-model.number='value'` 修改为数值类型
>   - `v-model.trim='value'` 忽略前面的和后面的空格
>   - `v-model.lazy='value'` 只在失去焦点的时候输出，将input事件转换为change事件
>

###   v-on

**鼠标触发属性**

```vue
<button v-on:click="num++">button</button>
<button @click="num++">button</button>
<button @submit.prevent="onSubmit">button</button>//提交事件但是不重载页面
```

**v-on的方法**

- .stop  阻止冒泡
- .prevent  阻止默认行为
- .self   只有事件本身可以触发

**修饰符的顺序很重要**

```js
@click.prevent.self  //阻止所有的点击
@click.self.prevent  //只会阻止对自身元素的点击
```

**按键触发属性**

```vue
<input type="password" name="ppe" id="ppe" @keydown.keya="handle"  v-model="pwd" />
//自定义鼠标按键
Vue.config.keyCodes.keya = 65
```

**可以用特殊变量`$event`传入方法**

```html
<button @click="handle('take it',$event)">点击出现奇迹</button>
```

```js
methods:{
    handle:function(msg,event){
        console.log(msg + event);
    }
}
```



### v-band

修改后面样式的值

- 修改url的值

```vue
<a v-band:href="url" >点击跳转</a>
//简写
<a :href="url" >点击跳转</a>
```

- 修改class类名
- 修改style属性值
- 绑定key

```vue
key: 帮助vue区分不同的元素，提高性能
<li :key= 'item.id' v-for='(item,index)in list'>{{item}} +'------'{{index}} </li> 
```

### v-if

(包括同类的v-else-if;v-else)
```vue
<div v-if="gotNum>10">    留下来</div>
<div v-else="gotNum<=10">滚粗</div>
```


### v-show

使用方法

```vue
<div v-show="got">
    留下来
</div>
//got 值为false时，
```

**注意**

v-if和v-show的区别，v-if是只在符合条件时显示，其它直接隐藏，v-show是在任何时间都会显示在html页面，只不过不会编译

### v-for

**遍历数组**

```vue
<div v-show="got" v-for="item in list">{{item}}</div>
//将对象传入数组，输出对应的对象的值
<div v-show="got" v-for="item in list">{{item.age +"-------"+item.name}}</div>
```

**遍历对象**(键值对)

```vue
//可以同时输出对象的键和对象的值
<div v-show="got" v-for="(value,key,index) in object">{{v+"-------"+k+"-------"+i}}</div>
```

> 算法的优化，可以在标签内部书写 `v-bind:key="item.id"`优化，简写`:key="item.id"`
>
> 当然也可以用`v-for="value of object"`