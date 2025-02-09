<template>
  <div>{{ label }} : {{ user.name }}</div>
  <div>{{ description }}</div>

  <button @click='submit'>Submit</button>
  <hr>
  <slot></slot>
</template>

<script>
import { computed, onMounted, ref, toRefs } from 'vue';
export default {
  props: {
    label: {
      type: String,
      default: ''
    },
    user: {
      type: Object,
      default: () => {}
    }
  },
  setup(props, { attrs, slots, emit }) {
    const { label, user } = toRefs(props);
    const description = computed(() => {
      return `${label.value} : ${user.value.name}`
    })

    onMounted(() => {
      // attrs digunakan untuk mengakses attribute yang ada di component
      // contoh attr digunakan untuk mengakses str='testing'
      console.log(attrs, 'Mounted');
      // slots digunakan untuk mengakses slot yang ada di component
      // contoh slots digunakan untuk mengakses <div>ini slots</div>
      console.log(slots, 'Mounted');
      console.log(emit, 'Mounted');
    })

    const submit = () => {
      // emit digunakan untuk mengirimkan data ke parent component
      emit('buatsubmitmanual', 'Data Submitted');
    }

    return { description, submit }
  }
}
</script>