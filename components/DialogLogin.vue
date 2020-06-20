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
        <v-tabs v-model="tab">
          <v-tab key="1">登陆</v-tab>
          <v-tab key="2">注册</v-tab>
        </v-tabs>
        <v-tabs-items v-model="tab">
          <v-tab-item key="1">
            <CardSignIn @submit="SignEvent"/>
          </v-tab-item>
          <v-tab-item key="2">
            <CardSignUp @submit="SignEvent"/>
          </v-tab-item>
        </v-tabs-items>
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
  import CardSignIn from "./CardSignIn";
  import CardSignUp from "./CardSignUp";
  export default {
    name: "CardLogin",
    components: {
      CardSignIn,
      CardSignUp,
    },
    data() {
      return {
        tab: null,
        dialog: false,
        authorization: false,
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
      }
    }
  }
</script>
