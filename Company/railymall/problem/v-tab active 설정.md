
### environment
1. 각 tab에는 query : { category: ${category.code} } 가 존재한다.
2. 전체 보기에는 query 가 없다. 
3. 각 tab 마다 query: { ...query , sort: "monthly, weekly, daily" } 가 붙는다.

### problem
1. 탭 이동은 active가 되지만 탭 내에서 정렬을 누르면 path가 달라져 active가 사라진다.
2.  active 방식을 method로 작성했지만 tab-primary로 어떻게 전달?
```vue
<template>
    <v-tabs grow>
        <tab-primary exact v-for="(item, index) in tabItems" :key="index" :to="item.to" :class="{ active: active(item) }">
            {{ item.text }}
        </tab-primary>
    </v-tabs>
</template>

<script>
    methods: {
        active(item){
            const isSamePath = this.$route.path == item.to.path;
            const isSameQuery = this.$route.query.category == item.to?.query?.category;
            return isSamePath && isSameQuery;
        }
    }
</script>
```
3. 현재 active는 category만 검사하는 것이라, 전체보기(쿼리 X) 는 active 될 수 없다.