<template>
  <div>
    <h1>Volunteer Activity Application</h1>
    <select v-model="rclass" @change="getStudent">
        <option value="1"></option>
        <option value="2"></option>
        <option value="3"></option>
    </select>
    <br>
    <ul>
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
      students: [],
      clsList: [
        { value: '1', text: 'ชั้นปีที่ 1' },
        { value: '2', text: 'ชั้นปีที่ 2' },
        { value: '3', text: 'ชั้นปีที่ 3' },
      ],
    }
  },
  watch: {
    rclass(){

    }
  },
  async created(){
    console.log('Ohhh!!! Created!!!!')
    this.getStudent()
    // // let res = await this.$http.get('/student?class=1' + this.rclass)
    // let res = await this.$http.get('/student', {params: {'class': this.rclass}})
    // this.student = res.data.student
  },
  methods: {
    async getStudent(){
    // let res = await this.$http.get('/student?class=1' + this.rclass)
    let res = await this.$http.get('/student', {params: {'class': this.rclass}})
    this.student = res.data.students
    },
  }, // methods
}
</script>

<template>
  
</template>
