<!--登录卡组件 TODO event-->
<template>
  <v-card>
    <v-card-text>
      <v-container>
        <v-row>
          <v-col cols="12">
            <v-text-field
              label="Username"
              hint="请输入用户名"
              clearable
              v-model="user.username"
            ></v-text-field>
          </v-col>
          <v-col cols="12">
            <v-text-field
              label="Password"
              :append-icon="pwdShow ? 'mdi-eye' : 'mdi-eye-off'"
              :type="pwdShow ? 'text' : 'password'"
              hint="请输入密码"
              @click:append="pwdShow = !pwdShow"
              v-model="user.password"
            ></v-text-field>
          </v-col>
        </v-row>
      </v-container>
    </v-card-text>
    <v-card-actions>
      <v-spacer/>
      <v-btn
        color="blue darken-1"
        text
        :loading="loading"
        @click="UserSignIn"
      >登录</v-btn>
      <v-btn
        color="blue darken-1"
        text
        @click="DialogClose"
      >取消</v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
  export default {
    name: "CardSignIn",
    data() {
      return {
        loading: false,
        pwdShow: false,
        user: {
          username: null,
          password: null,
        },
      }
    },
    created() {
    },
    methods: {
      UserSignIn:function() {
        this.loading=true
        setTimeout(()=>{
          this.loading=false
          this.$emit('submit',true)
          this.username=null
          this.password=null
        },2000)

      },
      DialogClose:function() {
        this.$emit('submit',false)
        this.username=null
        this.password=null
      }
    }
  }
</script>
