<template>
  <div>
    <form @submit.prevent="submitFunction">
      <input name="title" type="text" v-model="form.title"><br>
      <div v-if="errors.title">{{ errors.title }}</div>
      <input type="text" name="content" v-model="form.content"><br>
      <div v-if="errors.content">{{ errors.content }}</div>
      <button>送信</button>
    </form>
  </div>
</template>

<script setup>
  import {reactive} from 'vue'
  import {Inertia} from '@inertiajs/inertia'

  defineProps({
    errors: Object
  })

  const form = reactive({
    title: null,
    content: null
  })

  const submitFunction = () => {
    Inertia.post('/inertia',form)
  }
</script>

<style lang="scss" scoped>

</style>