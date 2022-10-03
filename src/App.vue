<script setup>
import { ref, computed } from 'vue';
const name = "Vue 3";
const counter = ref(0);
const arraynumeros = ref([]);

const increment = () => {
  counter.value++;
}

const decrementar = () => {
  counter.value--;
}

const reset = () => {
  counter.value = 0;
}

const add = () => {
  arraynumeros.value.push(counter.value);
};

const classCounter = computed(() => {
  if (counter.value === 0) {
    return 'zero';
  }
  if (counter.value < 0) {
    return 'negative';
  }
  if (counter.value > 0) {
    return 'positive';
  }
})

const blockAdd = computed(() => {
  if (arraynumeros.value.includes(counter.value)) {
    return true;
  }
});

</script>
  
<template>
  <div class="container text-center mt">
    <h1>{{name}}</h1>
    <h2 :class="classCounter">{{counter}}</h2>

    <div class="btn-group" role="group">
    <button @click="increment()" class="btn btn-success">aumentar</button>
    <button @click="decrementar()" class="btn btn-danger">decrementar</button>
    <button @click="reset()" class="btn btn-secondary">reset</button>
    <button @click="add()" :disabled="blockAdd" class="btn btn-primary">add</button>
    </div>
    
    <ul class="list-group">
      <li class="list-group-item" v-for="(numeros,index) in arraynumeros" :key="index">
        {{numeros}}
      </li>
    </ul>
  </div>
</template>
  
  
<style>
h1 {
  color: red;
}

.positive {
  color: green;
}

.negative {
  color: red;
}

.zero {
  color: peru;
}
</style>