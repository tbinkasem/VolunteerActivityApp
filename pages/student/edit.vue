<template>
  <div>
    <h1>Student Edit</h1>
    <v-text-field v-model="fname" label="ชื่อ" />
    <v-text-field v-model="lname" label="นามสกุล" />
    <v-btn @click="save">บันทึก</v-btn>
  </div>
</template>
<script>
// http://localhost:3000/#/student/edit?id=1
export default {
  data() {
    return {
      fname: '',
      lname: '',
    }
  },
  async created() {
    let res = await this.$http.get('/student/id/' + this.$route.query.id)
    this.fname = res.data.student.fname || ''
    this.lname = res.data.student.lname || ''
    // {
    //   ok: true,
    //   student: {
    //     id: 1,
    //     firstName: '',
    //     lastName: '',
    //     birth: '',
    //     class: 1,
    //   }
    // }
  },
  methods: {
    async save() {
      let res = await this.$http.post('/student/save', {
        id: this.$route.query.id,
        fname: this.fname,
        lname: this.lname,
      })
      if (!res.data.ok) {
        // TODO: แสดงข้อความ ว่าบันทึกไม่สำเร็จ
      } else {
        // TODO: แสดงข้อความ ว่าบันทึกสำเร็จ
      }
    },
  },
}
</script>