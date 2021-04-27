<template>
    <p/>
    <h1>{{newObj.day}}</h1> день
    <p>{{newObj.title}}</p>
</template>

<script>
import {ref, toRefs } from 'vue'
export default {
  name: "WrapperDay",

  props: {
    objectDate: Object
  },

  setup(props) {
    const newObj = toRefs(props).objectDate.value.value

    return {
      newObj
    }
  }
}
</script>

<style scoped>

</style>