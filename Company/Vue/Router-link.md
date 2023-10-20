
Vue 라이브러리 `VueRouter` 를 통해 `<router-link>` 를 사용하여 페이지를 이동할 수 있다.

target = "\_blank" 는 새 탭에 창을 이동시킨다.


```vue
//index.js
Vue.use(VueRouter);

const routes = [
	{ path: '/foo/:foo_id', component: ()=>import('../../../foo.vue')}
]

const router = new VueRouter({
	routes
})

,,
```


```vue
//route.vue

<router-link :to="`/foo/${fooId}`" target="_blank">
	<button>자세히 보기</button>
</router-link>

<script>
	data(){
		return{
			fooId:1
		}
	}
</script>
```
