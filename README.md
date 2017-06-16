# vue-spa-example

> A simple single page application example based on Vue2,requires additional installation of vue-resource

![](https://github.com/herozhou/vue-spa-example/blob/master/vue-spa-example/src/assets/img/appview.png)  

## Requirements
- vue: ^2.0.0
- vue-resource and vue-router

## Usage
### install

``` sh
 npm install vue-spa-example --save
```

### main.js

```javascript
import Vue from 'vue'
import App from './App'
import router from './router'

Vue.config.productionTip = false

/* eslint-disable no-new */
new Vue({
  el: '#app',
  router,
  template: '<App/>',
  components: { App } 
})

```

### index.js
> We use vue-resource here, so we need to install vue-resource first

```javascript
import Vue from 'vue'
import Router from 'vue-router'
import Home from '@/components/Home'
import Detail from '@/components/Detail'
import VueResource from 'vue-resource'  
Vue.use(VueResource)  
Vue.use(Router)

export default new Router({
  routes: [
    {
      path: '/',
      name: 'Hello',
      component: Home
    },
    {
    	path: '/detail/:id',
    	name: 'detail',
    	component: Detail
    },
    // { path: '*', redirect: '/' }
  ]
})


```

### App.vue
> Home.vue will show in <router-view>

```vue
<template>
  <div id="app">
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'app'
}
</script>
```

### Home.vue
> We get items from the server here

```vue
<!-- Home.vue -->
<template>
	<div class="container">
		<!-- 由于html不区分大小写，所以js中驼峰命名方式在html中要改成用短横线连接的形式 -->
		<home-header></home-header>
		<div class="content">
			<ul class="cont_ul">
				<list v-for="item in items" :price="item.price" :title="item.title" :img="item.img" >
				</list>
			</ul>
		</div>
	</div>
</template>

<script>
	// 导入要用到的子组件
	import HomeHeader from './HomeHeader'
	import List from './List'

	export default {
		data () {
			return {
				 items: []
				
			}
		},
		// 在components字段中，包含导入的子组件
		components: {
			HomeHeader,
			List
		},
		 // 在组件创建完成时，执行的钩子函数  
        created (){  
            // 在main.js里导入并使用vue-resource之后，就可以通过this.$http来使用vue-resource了，这里我们用到了get方法  
            this.$http.get('/api/books').then((data) => {  
                // 由于请求成功返回的是Promise对象，我们要从data.body.data拿到books数组  
                 this.items = data.body.data;  
            })  
        }  
	}
</script>
```


## Develop
```
npm run dev  //develop
npm run build //production
```


