<template>
  <v-list subheader nav>
    <v-subheader align="center">机器人列表</v-subheader>
    <!-- info bar -->
    <v-list-item>
      <v-list-item-action>ID</v-list-item-action>
      <v-list-item-content>State</v-list-item-content>
      <v-list-item-action>Ping&nbsp;&nbsp;&nbsp;</v-list-item-action>
    </v-list-item>
    <v-divider/>
    <!-- content -->
    <v-list-item-group @change="change_id">
      <template v-for="(item,index) in items">
        <v-list-item :key=index>
          <template>
            <v-list-item-action>
              <v-list-item-title v-text="item.ID"/>
            </v-list-item-action>
            <v-list-item-content>

            </v-list-item-content>
            <v-list-item-action>
              <v-chip
                outlined
                color="green"
                v-if="item.ping < 200"
              >{{item.ping}}ms</v-chip>
              <v-chip
                outlined
                color="orange"
                v-else-if="item.ping >= 200 && item.ping <500"
              >{{item.ping}}ms</v-chip>
              <v-chip
                outlined
                color="red"
                v-else
              >{{item.ping}}ms</v-chip>
            </v-list-item-action>
          </template>
        </v-list-item>
      </template>
    </v-list-item-group>
  </v-list>
</template>

<script>
  export default {
    name: "ListRobots",
    data() {
      return {
        items: [
          {
            ID: 1,
            ping: 60
          },
          {
            ID: 2,
            ping: 300
          },
          {
            ID: 3,
            ping: 999
          },
        ],
      }
    },
    methods:{
      change_id:function (val) {
        this.$router.push({
          path: '/',
          query: {
            id: val
          }
        })
      },
    },
    computed:{

    }
  }
</script>
