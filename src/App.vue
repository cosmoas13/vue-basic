<template>
  <UserComponent 
    :label='label' 
    :user='user'  
    str='testing' 
    @buatsubmitmanual='onSubmit'>
    <div>ini slots</div>
  </UserComponent>
  <br>
  <button @click='changeName'>Change</button>
</template>

<script>
import { 
  ref,
  reactive
} from 'vue';
import UserComponent from './components/UserComponent.vue';
export default {
  // component digunakan untuk memanggil component yang ada di dalam setup
  components: {
    UserComponent
  },
  setup() {
    const label = ref('biodata');
    const user = reactive({
      name: 'John Doe',
      age: 25,
    })

    const changeName = () => {
      user.name = 'Henshin Name'
    }

    const onSubmit = (data) => {
      console.log(data);
    }

    return { 
      label,
      user,
      changeName,
      onSubmit
    };
  }
}
</script>