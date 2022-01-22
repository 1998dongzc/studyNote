# Vue.js

### 1.v-cloak

```vue
直接用于元素上 如 <h1 v-cloak/>
[v-cloak]:{
	dispaly:none
}
```

> 在VM未生成，无法渲染解析元素时,不会操作。VM开始接管后，删除所有元素中的v-cloak，配合CSS的display：none，让因为网络等原因的无法渲染的元素隐藏，一旦VUE可以编译渲染元素，便让其展示。