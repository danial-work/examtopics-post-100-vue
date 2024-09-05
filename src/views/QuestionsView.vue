<script setup>
import { useRoute } from 'vue-router'
import { ref } from 'vue'
import json from '../assets/questions.json'
import QuestionComponent from '@/components/QuestionComponent.vue'

const route = useRoute();
console.log(route);

const q_json = json;
const q_json_ref = ref(q_json);
console.log(q_json);
console.log(q_json_ref);

const size = 10;
const q_items = Array.from({ length: Math.ceil(q_json.length / size) }, (v, i) =>
  q_json.slice(i * size, i * size + size)
);
const q_items_ref = ref(q_items);
</script>

<template>
  <nav>
    <span v-for="(item, index) in q_items_ref" :key="index">
      <router-link :to="'/question/' + $route.params.mode + '/' + Object.keys(item[0])[0] + '/' +  Object.keys(item[item.length - 1])[0]">{{ Object.keys(item[0])[0] }} - {{ Object.keys(item[item.length - 1])[0] }}</router-link><span v-if="index < q_items_ref.length - 1"> | </span>
    </span>
    
  </nav>
  <div>
    <h1 v-if="$route.params.mode == 'item'">Questions</h1>
    <h1 v-else>Questions - List</h1>
    <div v-if="$route.params.q_num_s>=100 && $route.params.q_num_e<=311">
      <QuestionComponent v-for="(n ,i) in $route.params.q_num_e-$route.params.q_num_s+1" :key="i" :q_n="parseInt($route.params.q_num_s)+i" :q_l="q_json_ref[parseInt($route.params.q_num_s)+i-100]" :mode="$route.params.mode"/>
    </div>
    <div v-else>
      <p>Out of bounds</p>
    </div>
  </div>
  <nav v-if="$route.params.mode == 'item'">
    <span v-for="(item, index) in q_items_ref" :key="index">
      <router-link :to="'/question/' + $route.params.mode + '/' + Object.keys(item[0])[0] + '/' +  Object.keys(item[item.length - 1])[0]">{{ Object.keys(item[0])[0] }} - {{ Object.keys(item[item.length - 1])[0] }}</router-link><span v-if="index < q_items_ref.length - 1"> | </span>
    </span>
    
  </nav>
</template>