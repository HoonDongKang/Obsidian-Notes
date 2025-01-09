
### Enviroment

`FilteringList` : 필터링 설정하는 페이지
	- `filteringForm` : 필터링 폼
		 -  `FilteringKeyProps` : 필터링 폼 키 component
		 -  `FilteringValueProps` : 필터링 폼 값 component

1. 필터링을 설정하는 관리자 페이지에서 `filteringForm` 을 통해 `type` 을 설정
2. `type = key / value` 에 따라 `FilteringKeyProps` / `FilteringValueProps` 렌더링
3. `filteringForm` 에서 `initValue` 를 설정해서 props로 보내준다.

```javascript
// filteringForm.vue
export const initForm = (form = {}) => ({
    ...form,
    type: form?.type || "key",
    name: form?.name || null,
    code: form?.code || null,
    desc: form?.desc || null,
});

// FilteringKeyProps / FilteringValueProps
<script>
import { initForm } from "./filteringForm.vue";

methods: {
	sync() {
		this.form = initForm(this.value);
	},
}
</script>
```


### Issue

로컬에서는 문제없이 동작하지만 배포된 페이지에서 오류 발생

**`Uncaught (in promise) ReferenceError: Cannot access 'E' before initialization`**

변수 선언 전에 접근하는 이슈로 참조 불가

### Solve

부모 컴포넌트 `filteringForm` 에서 선언한 변수 `initForm`을 export하여
자식 컴포넌트 `FilteringKeyProps / FilteringValueProps` 에서 import하여 사용하고 있는 상태.

하지만 
`initForm`은 익명 함수로 선언되어 변수에 할당된 상태
함수 선언문은 런타임 이전에 호이스팅으로 함수 객체가 선언되어 있지만,
함수 표현식은 변수에 할당된 상태이기 때문에 호이스팅은 변수로 런타임 전에 선언된다.

하지만 해당 변수는 `const`로 선언되어 있기 때문에 할당되기 전에 TDZ에 들어가 있고, 
TDZ에 들어가 있는 상태에서 import 하려다 보니 Access할 수 없는 이슈가 발생

-> 함수 선언문 function 으로 선언하던가 
/ var 로 선언하던가 
/ 자식 컴포넌트에서 새로 변수를 생성하던가