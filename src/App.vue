<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <h1>{{count}}</h1>
  <h1>{{double}}</h1>
  <ul>
    <li v-for="num in number" :key="num">{{num}}</li>
  </ul>
  <h1>{{person.name}}</h1>
  <button @click="increase">INCREASE</button>
</template>

<script lang="ts">
import { defineComponent, reactive, computed, toRefs } from 'vue';
interface DataProps {
  count: number;
  double: number;
  increase: () => void;
  number: number[];
  person: { name?: string};
}

export default defineComponent({
  name: 'App',
  setup() {
    const data: DataProps = reactive({
      count: 0,
      increase: () => { data.count++ },
      double: computed(() => data.count * 2),
      number: [0, 1, 2, 3],
      person: {}
    })
    data.number[0] = 5
    data.person.name = "kkk"
    const refData = toRefs(data)
    return{
      ...refData
    }
  }
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
