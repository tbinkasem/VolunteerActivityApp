<template>
  <div>
      <h1>Hello {{name}} </h1>
      <input type="text" :value="name">
  </div>
</template>
<script>
export default {
  data(){
      setInterval(() => {
        this.name += '*' 
      } ,1000)
      return {
        name: 'Narupon Noothong Lpt..'
      }
  }
}
</script>

