<!--用户管理相关功能组件 TODO Authorization-->
<template>
  <div>
    <v-dialog v-model="dialog" persistent max-width="350" v-if="!authorization">
      <!-- sign in button -->
      <template v-slot:activator="{ on }">
        <v-btn text v-on="on">登录</v-btn>
      </template>
      <!-- sign dialog -->
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
    </v-dialog>
    <!-- account button -->
    <v-menu bottom offset-y v-if="authorization">
      <template v-slot:activator="{ on }">
        <v-btn color="teal" icon v-on="on">
          <v-icon>mdi-account-circle</v-icon>
        </v-btn>
      </template>
      <v-list>
        <v-list-item
          @click="SignOut">
          <v-list-item-title>登出</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-menu>
  </div>
</template>

<script>
  export default {
    name: "CardLogin",
    components: {
    },
    data() {
      return {
        tab: null,
        dialog: false,
        authorization: false,
        loading: false,
        pwdShow: false,
        user: {
          username: null,
          password: null,
        },
      }
    },
    props: {
    },
    methods: {
      SignEvent:function (msg) {
        this.dialog=false;
        this.authorization=msg;
      },
      SignOut:function () {
        this.authorization=false;
      },
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
