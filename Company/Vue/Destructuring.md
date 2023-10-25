
기본적인 Destructuring
```javascript
const obj= {
	a: 'hello',
	b: 'my name is',
	c: 'Dong Hoon'
};

const {a, b, c} = obj;
// a= 'hello',
// b= 'my name is',
// c= 'Dong Hoon'
```

Nested Obj Destructuring
```javascript
const nestObj= {
	name: {
		first: 'Dong Hoon',
		last: 'Kang'
	},
	greet: 'hello'
};

const { name:{ first, last }, greet} = nestObj;
// first= 'Dong Hoon',
// last= 'Kang',
// greet= 'hello'
```

Destructuring with Default Props
```javascript
const defaultObj= {
	name: {
		first: 'Dong Hoon',
		last: 'Kang'
	},
	greet: 'hello'
};

const {
	name: { nation } = { nation: 'Korea'}
}= defaultObj;
```

+++
v-bind 와 같은 attribute 에 객체 형식의 속성값을 할당하려면 

```
v-bind ="{ property1, property2 }"
```

형식을 가지지만, 만약 property1 이 더 깊은 depth를 가지고, 그 밑 property를 할당해주려면

```
v-bind = "{ "property1":property1.proproperty, property2 }"
```

로 할당해줄 수 있다.