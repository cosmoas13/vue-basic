<template>
  <div>Count: {{ nilai }}</div>
  <button @click='add'>ADD</button>
</template>

<script>
import { ref, reactive, watchEffect, toRefs } from 'vue';
export default {
  setup() {
    const counter = reactive({
      nilai: 0,
      foo: 'bar'
    });
    const add = () => {
      counter.nilai++;
    }
    watchEffect(() => {
      // tidak akan berjalan saat log foo
      // karena foo nilainya tidak berubah
      console.log('nilai berubah', counter.nilai);
    }, {
      // flush digunakan untuk menentukan kapan watchEffect dijalankan
      flush: 'post', // post, pre, sync
      // onTrigger digunakan untuk mengetahui kapan watchEffect dijalankan
      onTrigger: (event) => {
        console.log('trigger', event);
      },
      // onTrack digunakan untuk mengetahui kapan reactive diakses
      onTrack: (event) => {
        console.log('track', event);
      }
    });
    return { 
      add,
      ...toRefs(counter),
    };
  }
}
</script>
