Parent component -> Child component : $emit
Child component -> Parent component : props

``` vue
//Parent Component
<template>
	<div>
		<ChildComponent :filter="filter" @after="renewFilter(data)">
		</ChildComponent>
	</div>
</template>

<script>
export default {
	components:{
		ChildComponent
	},
	data(){
		return{
			filter:'before'
		}
	},
	mehtods:{
		renewFilter(data){
			// before -> changed
			this.filter = data
		}
	}
}

</script>

```


``` vue
//Child Component
<template>
	<div>
		{{filter}}
	</div>
	<button @click="changeFilter">Change!</button>
</template>

<script>
export default {
	props:['filter'],
	methods:{
		changeFilter(){
			this.$emit('After','Changed!')
		}
	}
}

</script>

```

