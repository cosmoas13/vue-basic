<template>
  <div>Count: {{ nilai }}</div>
  <button @click='add'>ADD</button>
</template>

<script>
import { ref, reactive, watch, toRefs } from 'vue';
export default {
  setup() {
    const counter = reactive({
      nilai: 0,
      foo: 'bar'
    });
    const num1 = ref(1);
    const num2 = ref(2);
    const add = () => {
      counter.nilai++;
      // num1.value++;
      // num2.value++;
    }

    // cocok untuk ref primitive data
    // watch(() => num1.value, (newValue, oldValue) => {
    //   console.log('num1 berubah', newValue, oldValue);
    // });

    // watch([num1, num2], (dataBaru, dataLama) => {
    //   console.log(num1.value);
    //   console.log(num2.value);
    // })

    watch(() => counter.nilai, (newValue, oldValue) => {
      console.log('nilai berubah', newValue, oldValue);
    }, {
      // immediate digunakan untuk menjalankan watch saat pertama kali
      immediate: true,
      // deep digunakan untuk mengecek perubahan pada object dalam object
      deep: true
    });

    return { 
      add,
      ...toRefs(counter),
    };
  }
}
</script>
