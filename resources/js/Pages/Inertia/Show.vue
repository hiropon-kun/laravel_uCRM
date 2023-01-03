<template>
  <div>
    {{ id }}<br>
    {{ blog.title }}<br>
    <button @click="deleteConfirm(blog.id)">削除</button>
  </div>
</template>

<script setup>
  import {Inertia} from '@inertiajs/inertia'

  defineProps({
    id : String,
    blog: Object
  })

  const deleteConfirm = id => {
    // console.log(id)
    Inertia.delete(`/inertia/${id}`,{
      onBefore: () => confirm('本当に削除しますか?')
    })
  }
</script>

<style lang="scss" scoped>
  
</style>