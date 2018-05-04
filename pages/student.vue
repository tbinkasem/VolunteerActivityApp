<template>
  <div>
    <h1>Volunteer Activity Application</h1>
    <ul>
      <select v-model="rclass" @change="getStudent">
        <option value="1"></option>
        <option value="2"></option>
      </select>
      <li v-for="st in students" :key="st.ids">
        {{ st.ids }}<br>
        {{ st.fname }}<br>
        {{ st.lname }}
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  data() {
    return {
      rclass: '1',
      student: [],
    }
  },
  async created(){
    console.log('Ohhh!!! Created!!!!')
    // // let res = await this.$http.get('/student?class=1' + this.rclass)
    // let res = await this.$http.get('/student', {params: {'class': this.rclass}})
    // this.student = res.data.student
  },
  methods: {
    getStudent(){
      console.log('Ohhh!!!')
    // let res = await this.$http.get('/student?class=1' + this.rclass)
    let res = await this.$http.get('/student', {params: {'class': this.rclass}})
    this.student = res.data.student
    },
  }, // methods
}
</script>

<template>
  
</template>
