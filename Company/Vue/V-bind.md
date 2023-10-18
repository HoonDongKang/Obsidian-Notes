하나 이상의 속성 또는 컴포넌트 prop을 표현식에 동적으로 바인딩할 때 사용한다. 

``` vue
<template>
    <div>
        <div :style="{color:bindingClass?'red':'blue'}">hello</div>
        <button @click="changeBind">Click</button>
    </div>
</template>

<script>
export default {
    data(){
        return{
            bindingClass: true
        }
    },
    methods:{
        changeBind(){
            this.bindingClass = !this.bindingClass
        }
    }
}
</script>
```

button 을 클릭할 때마다, `bindingClass`는 true 또는 false로 변환이 되며 이 데이터가 바인딩된 `hello` 의 색깔은 빨강과 파랑으로 변환된다.

v-bind는 `src` `class` `style` `href` 와 같은 속성 뿐만 아니라 props 데이터를 전달해주기도 한다.

```vue
// Parent Component
<template>
  <div id="app">
    <VBind :title="propsData.title" :content="propsData.content"/>
  </div>
</template>

<script>
import VBind from './components/VBind.vue'

export default {
  name: 'App',
  components: {
    VBind
  },
  data(){
    return{
      propsData:{
        title:'prop title',
        content:'prop content'
      }
    }
  }
}
</script>
```

```vue
//child component
<template>
    <div>
        <!-- <div :style="{color:bindingClass?'red':'blue'}">hello</div>
        <button @click="changeBind">Click</button> -->
        <p>title : {{title}}</p> <!--title : prop title-->
        <p>content : {{content}}</p> <!--content : prop content-->
    </div>
</template>

<script>
export default {
    data(){
        return{
            bindingClass: true
        }
    },
    props:['title', 'content'],
    methods:{
        changeBind(){
            this.bindingClass = !this.bindingClass
        }
    }
}
</script>
```

하지만 위 같은 경우에 `:title` `:content` 두 가지 데이터만 바인딩을 해주었지만, 실제로 수많은 데이터를 객체 형태로 전달해줄 경우, 데이터 하나씩 바인딩을 해줄 수 없다. 그러기 위해 나온 것이
`v-bind = {data}` 이다.

```vue
<template>
  <div id="app">
    <!-- <VBind :title="propsData.title" :content="propsData.content"/> -->
    <VBind v-bind="propsData"/>
  </div>
</template>
<script>

import VBind from './components/VBind.vue'
export default {
  name: 'App',
  components: {
    VBind
  },
  data(){
    return{
      propsData:{
        title:'prop title',
        content:'prop content'
      }
    }
  }
}
</script>
```

```vue
<template>
    <div>
        <!-- <div :style="{color:bindingClass?'red':'blue'}">hello</div>
        <button @click="changeBind">Click</button> -->
        <p>title : {{title}}</p>
        <p>content : {{content}}</p>
    </div>
</template>
<script>

export default {
    data(){
        return{
            bindingClass: true
        }
    },
    // props:['title','content'],
    props:{
        title:{type: String, default: null},
        content:{type: String, default: null}
    },
    methods:{
        changeBind(){
            this.bindingClass = !this.bindingClass
        }
    }
}
</script>
```

