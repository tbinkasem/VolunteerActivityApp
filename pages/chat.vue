<template>
    <div>
        <h1>Check in Room</h1>
        <div>
            <v-text-field label="Name" v-model="name" />
            <v-text-field label="Text" v-model="text" />
            <v-btn @click="send">Send</v-btn>
        </div>
        <ul>
            <li v-for="(m, idx) in msg" :key="idx">
                <b>{{ m.name }}</b> Say: {{ m.text }}
            </li>
        </ul>
    </div>
</template>

<script>
export default {
  data(){
      return {
          name: '',
          text: '',
          msg: [],
      }
  },//end data

  created(){
      this.$socket.subscribe('room39',this.onMsg)
  },//subcribe

  beforeDestroy(){
      this.$socket.unsubscribe('room39')
  },//unsubscribe

  methods: {
      send(){
          this.$socket.publish('room39', {
              name: this.name,
              text: this.text,
          })
      },
      onMsg(data){
          console.log(data)
          this.msg.unshift(data)
      },
  }, //end methods
}
</script>
