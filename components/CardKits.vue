<template>
  <v-card class="px-2">
    <v-row>
      <v-col cols="auto">
        <v-btn
           color="teal"
           :loading="loader_mode"
           @click="change_mode"
        >
          <v-icon>{{mode_auto?auto.icon:control.icon}}</v-icon>
          {{mode_auto?auto.text:control.text}}
        </v-btn>
      </v-col>
      <v-col cols="auto">
        <v-btn :disabled="mode_auto"><v-icon>mdi-arrow-up-bold</v-icon>向上</v-btn>
      </v-col>
      <v-col cols="auto">
        <v-btn
          :color=state_running?stop.color:start.color
          :loading="loader_state"
          @click="change_state"
        >
          <v-icon>{{state_running?stop.icon:start.icon}}</v-icon>
          {{state_running?stop.text:start.text}}
        </v-btn>
      </v-col>
      <v-spacer/>
    </v-row>
    <v-row>
      <v-col cols="auto">
        <v-btn :disabled="mode_auto"><v-icon>mdi-arrow-left-bold</v-icon>向左</v-btn>
      </v-col>
      <v-col cols="auto">
        <v-btn :disabled="mode_auto"><v-icon>mdi-arrow-down-bold</v-icon>向下</v-btn>
      </v-col>
      <v-col cols="auto">
        <v-btn :disabled="mode_auto"><v-icon>mdi-arrow-right-bold</v-icon>向右</v-btn>
      </v-col>
      <v-spacer></v-spacer>
    </v-row>
  </v-card>
</template>

<script>
  export default {
    name: "CardKits",
    data: function () {
      return {
        // sign robot control mode
        mode_auto: true,
        // sign robot running state
        state_running: true,
        // loader
        loader_mode: false,
        loader_state: false,
        auto: {
          text: '自动',
          icon: 'mdi-autorenew'
        },
        control: {
          text: '遥控',
          icon: 'mdi-google-controller'
        },
        stop:{
          text: '停止',
          icon: 'mdi-stop',
          color: 'error'
        },
        start:{
          text: '启动',
          icon: 'mdi-play',
          color: 'primary'
        }
      }
    },

    props:{
      size_desktop: Boolean,
    },

    methods:{
      change_mode:function () {
        this.loader_mode = true
        setTimeout(() => {
          this.loader_mode = false
          this.mode_auto =! this.mode_auto
          },
          500)
      },
      change_state:function () {
        this.loader_state = true
        setTimeout(() => {
          this.loader_state = false
          this.state_running =! this.state_running
          },
          500)
      }
    }
  }
</script>
