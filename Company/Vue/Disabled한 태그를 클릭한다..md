##### <font color="#ccc1d9">요구사항</font>

'카카오톡 수령' 탭은 연락처와 카카오톡 아이디, 두 가지 `input` 이 존재하며 하나를 선택하여 사용자는 입력하게 된다.

	조건 1. 두 input의 type은 모두 text 이다.
	조건 2. 사용자는 하나의 input에만 데이터를 전달할 수 있다.

##### <font color="#ccc1d9">해결과정</font>

첫 번째 실패 : 하나의 `input`을 클릭하면 event 를 통해 다른 `input` 을 disabled 상태로 변환시킨다. 

```vue
<template>
    <div>
        <div>
            <input v-model="form.id" :disabled="this.form.idOrPhone === 'phone'"  @click="disabled()"  placeholder="카톡 아이디"/>
        </div>
        <div>
            <input v-model="form.phone" :disabled="this.form.idOrPhone === 'id'" @click="disabled()" placeholder="전화번호"/>
        </div>
    </div>
</template>

<script>
export default{
    data(){
        return{
            form:{
                idOrPhone:'id',
                id:null,
                phone:null,
            }
        }
    },
    methods:{
        disabled(){
	      this.form.idOrPhone=== 'id' ? this.form.idOrPhone= 'phone' : this.form.idOrPhone= 'id'
        }
    }
}
</script>
```

- 단순히 클릭 시 반대 `input` 만 `disabled`를 시킬 뿐, 그 외 기능을 수행할 수가 없다.
- `disabled` 를 클릭하면 활성화된 `input`을 `disabled`로 변환시키고 싶었는데, 반대로 동작된다.
- 중요한 것은 `disabled` 한 상태에서 클릭 이벤트가 발생하지 않는다는 것.

결국 두 가지 `input` 만으로 이벤트를 통해 활성화 / 비활성화를 구현하기 힘들겠다는 생각에,
 행동을 결정할 토글을 추가하기로 결정하였다.

```vue
<template>
    <div>
        <input id="id" type="radio" value = "id" v-model="form.idOrPhone">
        <label for="checked">아이디</label>
        <input id="phone" type="radio" value = "phone" v-model="form.idOrPhone">
        <label for="phone">전화번호</label>
        <div>
            <input v-model="form.id" :disabled="this.form.idOrPhone === 'phone'"  placeholder="카톡 아이디"/>
        </div>
        <div>
            <input v-model="form.phone" :disabled="this.form.idOrPhone === 'id'" placeholder="전화번호"/>
        </div>
    </div>
</template>

<script>
export default{
    data(){
        return{
            form:{
                idOrPhone:'id',
                id:null,
                phone:null,
            }
        }
    },
}
</script>
```

##### <font color="#ccc1d9">회고</font>
<u>추가적인 태그의 생성으로 기능을 조작하는 것</u>보다
<u>기존의 태그들을 활용하여 새로운 메서드</u>로 요구사항을 해결하는 것이 
더 유용하고 효율적이라는 생각에 `radio` 를 사용하고 싶지 않았었다. 

하지만 직접 DOM을 조작해가며 상태를 변화시키는 것보다는 새로운 태그로 이벤트를 발생시켜
조건을 변경시키는 것이 더 효율적이고 안정적인 방법인 것 같다.