<template>
  <v-app>
    <!-- header bar -->
    <v-app-bar app clipped-right>
      <v-toolbar-title v-text="title"/>
      <v-spacer />
      <!-- login component -->
      <DialogLogin/>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
    </v-app-bar>

    <!-- content -->
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>

    <!-- footer bar -->
    <v-footer app>
      <v-icon small :color=state_color>mdi-checkbox-blank-circle</v-icon>
      <span class="font-weight-light">{{state_text}}</span>
      <v-spacer />
      <span class="text--disabled">{{footer}}</span>
    </v-footer>

    <!-- navigation side bar -->
    <v-navigation-drawer
      app
      right
      clipped
      v-model="drawer"
    >
      <ListRobots/>
      <template v-slot:append>
        <div class="pa-2">
          <v-btn block outlined color="indigo" to="/settings">
            <v-icon>mdi-cog</v-icon>settings
          </v-btn>
        </div>
      </template>
    </v-navigation-drawer>
  </v-app>
</template>

<script>
  import DialogLogin from "../components/DialogLogin";
  import ListRobots from "../components/ListRobots";

  export default {
    components: {
      DialogLogin,
      ListRobots,
    },
    data () {
      return {
        title: 'Calf机器人管理平台',
        footer: 'Designed by YuTang',
        drawer: true,
        selected: null,
        connect_state: 1,
      }
    },
    methods:{
    },
    computed:{
      state_color:function () {
        if (this.connect_state === 1)
          return 'green'
        else if (this.connect_state === 2)
          return 'yellow'
        else return 'red'
      },
      state_text:function () {
        if (this.connect_state === 0)
          return 'server disconnected'
        else return 'server connected'
      }
    },
  }
</script>
