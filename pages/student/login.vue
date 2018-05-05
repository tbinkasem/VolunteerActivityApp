<template>
<div id="app">
  <v-app id="inspire">
    <v-content>
      <v-container fluid fill-height>
        <v-layout align-center justify-center>
          <v-flex xs12 sm8 md4>
            <v-card class="elevation-12">
              <v-toolbar dark color="primary">
                <v-toolbar-title>เข้าสู่ระบบ</v-toolbar-title>
                <v-spacer></v-spacer>
                <v-tooltip bottom>
                  <v-btn
                    icon
                    large
                    :href="source"
                    target="_blank"
                    slot="activator"
                  >
                    <v-icon large>code</v-icon>
                  </v-btn>
                  <span>Source</span>
                </v-tooltip>
              </v-toolbar>
              <v-card-text>
                <v-form>
                  <v-text-field prepend-icon="person" name="username" label="Login" type="text" />
                  <v-text-field prepend-icon="lock" name="password" label="Password" id="password" type="password" />
                </v-form>
              </v-card-text>
              <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn color="primary" @click="onSuccess">Login</v-btn>
              </v-card-actions>
            </v-card>
          </v-flex>
        </v-layout>
      </v-container>
    </v-content>
  </v-app>
</div>
</template>

<style>
  body{
    background: #666 !important;
  }
</style>

<script>

export default {
  data () {
    drawer: null
    return {
      model: {
        username: 'admin',
        password: '123456'
      },

      fields: {
        username: { label: 'Username' },
        password: { label: 'Password', type: 'password' }
      },
      show: true
    }
  },
  methods: {
    onSuccess (data) {
      this.$store.commit('setAuth', data)
      this.$router.replace('/student')
    }
  },

  mounted () {
  }
}
</script>

<style scoped>
.red{
  color: blueviolet;
}
</style>