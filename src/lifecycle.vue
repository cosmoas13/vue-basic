<template>
  <div>Count: {{ nilai }}</div>
  <button @click='add'>ADD</button>
</template>

<script>
import { 
  onBeforeMount, 
  onMounted, 
  onBeforeUpdate, 
  onUpdated, 
  onBeforeUnmount,
  onActivated,
  onDeactivated,
  onErrorCaptured 
} from 'vue';
export default {
  setup() {
    return { 
    };
  }
}
</script>
