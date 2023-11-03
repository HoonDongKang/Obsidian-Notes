
`<slot>`은 부모가 제공한 slot content가 렌더링 될 위치를 의미 ( slot outlet )

```vue
// Parenet-comp
<FancyButton>
	클릭하기---- slot content
</FancyButton>
```
```vue
// Child-comp
<button>
	<slot></slot>---- slot outlet
</button>
```

parent comp 페이지에서는 "클릭하기"라는 버튼을 생성하게 된다.
-  slot content를 부모에서 작성하여, 자식에 있는 slot outler을 통해 생성한다.
-  텍스트 뿐만 아니라 모든 형태가 유효


```vue
//parent-comp
<template>
  <div id="app">
    <slot-component-vue>
       <template #button>
         이건 버튼이여
       </template>
       <template #checkbox>
         이건 체크여
       </template>
       <template #textfield>
         이건 텍스트여
       </template>
    </slot-component-vue>
  </div>
</template>
```

```vue
//child-comp
<template>
    <div>
        <button>
            <slot name="button">
            </slot>
        </button>
        <input type="checkbox">
            <slot name="checkbox"></slot>
        <input type="text">
            <slot name="textfield"></slot>
    </div>
</template>
```

- slot에 name을 지정해서 slot outlet을 지정하여 content를 생성할 수 있다.
-  v-slot: name => \#name
- name 설정 안하면 내부적으로 "default" 로 지정

```vue
// parent-comp
<slot-component-vue>
  <template #activator={last,first}>
    {{last}} {{first}}
  </template>
</slot-component-vue>
```
```vue
// child-comp
<template>
    <div>
        <slot name="activator" :first="name.first" :last="name.last"></slot>
    </div>
</template>

<script>
export default {
    data:()=>({
        name:{
            first: "Daniel",
            last: "Kang"
        }
    })
}
</script>
```

- 기본적으로 parent component는 child component의 데이터를 다른 이벤트(prop, emit이나)없이 조회할 수 없다.
- 이 조건은 slot에서도 마찬가지지만, v-bind를 통해 조회할 수있는 방법이 있다.
- 자식에서 전달할 data를 선언 후, slot content에 prop으로 바인딩해준다.
- 부모에서는 해당 name의 템플릿을 불러온 후, 바인딩된 데이터를 destructuring을 통해 가져올 수 있다.