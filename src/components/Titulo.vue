<template>
  <h2>{{ message }}</h2>
</template>

<script>
export default {
    name: 'Titulo',
    props: {
        message: String
    }


}
</script >
  

<style scoped>
  h2 {
    color: peru;
  }
</style>