<template>
  <div>
    <h1>{{ message }}</h1>
    <div>Name: {{ name }}</div>
    <div>Age: {{ age }}</div>
  </div>
  <br>
  <div>
    <span><strong>hitung</strong></span>
    <div>Count : {{ nilai }}</div>
    <button @click='add'>ADD</button>
  </div>
  <br>
  <div>
    <div>{{ result }}</div>
  </div>
</template>

<script>
import { ref, reactive, computed, toRefs } from 'vue';
export default {
  setup() {
    // ref untuk data primitive
    const message = ref('belajar composition api vue 3');
    // reactive untuk data object
    const user = reactive({ 
      name: 'John Doe', 
      age: 25 
    });
    const counter  = ref(0);
    const counterReact = reactive({
      nilai: 0,
    })
    // setTimeout(() => {
    //   user.name = 'Jane Doe';
    // }, 2000);

    // method
    const add = () => {
      // counter.value++;
      // set value pada result seperti ref
      result.value = 2;
      counterReact.nilai++;
    }

    const addNum = ref(1);

    // computed digunakan untuk menghitung hasil dari data reactive
    // const result = computed(() => counterReact.nilai + addNum.value)
    // bentuk computed getter dan setter
    const result = computed({
      get() {
        return counterReact.nilai + addNum.value
      },
      set(value) {
        addNum.value = value
      }
    })

    return { 
      message, 
      // toRefs untuk mengembalikan object reactive menjadi primitive
      ...toRefs(user),
      add,
      ...toRefs(counterReact),
      result
    };
  }
}
</script>
