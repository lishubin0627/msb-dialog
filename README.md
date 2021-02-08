npm地址：https://www.npmjs.com/package/msb-dialog
# msb-dialog
uniapp dialog插件
## 使用方法

 1. mine.js中全局引用

```javascript

//请求加载组件
import msbDialog from '../components/msb-dialog/msb-dialog.vue';
import menuDialog from '../components/menu-dialog/menu-dialog.vue';
//组件挂载到全局，方便每个页面使用
Vue.component('msbDialog ', msbDialog );
Vue.component('menuDialog ', menuDialog );
```

```bash
<msb-dialog ></msb-dialog >
<menu-dialog ></menu-dialog >
```

 1.单页面引用
 

```javascript
import msbDialog from '../components/msb-dialog/msb-dialog.vue';
import menuDialog from '../components/menu-dialog/menu-dialog.vue';
components: {
		msbDialog,
		menuDialog
	},
```

```javascript
<msb-dialog ></msb-dialog >
<menu-dialog ></menu-dialog >
