<!-- index page -->
<template>
  <div>
    <!-- content layout -->
    <v-row justify="center">
      <v-col cols="12" lg="9" xl="8">
        <!-- the navigation and monitor card -->
        <v-card>
          <v-tabs v-model="tab">
            <v-tab><v-icon>mdi-directions-fork</v-icon>导航</v-tab>
            <v-tab><v-icon>mdi-video</v-icon>监控</v-tab>
          </v-tabs>
          <v-tabs-items v-model="tab">
            <v-tab-item>
              <v-responsive :aspect-ratio="ratio">
                <span>map area</span>
              </v-responsive>
            </v-tab-item>
            <v-tab-item>
              <v-responsive :aspect-ratio="ratio">
                <CardMonitor/>
              </v-responsive>
            </v-tab-item>
          </v-tabs-items>
        </v-card>
      </v-col>
      <!-- kits card (desktop layout) -->
      <v-col lg="3" xl="3" v-if="size_desktop">
        <CardConsole/>
      </v-col>
    </v-row>
    <v-row justify="center">
      <!-- kits card (mobile layout) -->
      <v-col v-if="!size_desktop">
        <CardConsole/>
      </v-col>
      <v-col xl="11">
        <CardKits/>
      </v-col>
      <v-col>
        <CardInfo/>
      </v-col>
    </v-row>
  </div>
</template>

<script>
  import CardConsole from "../components/CardConsole";
  import CardKits from "../components/CardKits";
  import CardInfo from "../components/CardInfo";
  import CardMap from "../components/CardMap";
  import CardMonitor from "../components/CardMonitor";

  export default {
    components: {
      CardConsole,
      CardKits,
      CardInfo,
      CardMap,
      CardMonitor
    },
    data: function () {
      return {
        // current tab index
        tab: null,
        // video and map canvas ratio
        ratio: 16 / 9,
        // viewport size type
        size_desktop: true,
      }
    },
    props:{
      selected:Int8Array
    },
    watch:{

    },
    computed:{
      layoutChange:function () {
        this.size_desktop = this.$vuetify.breakpoint.lg || this.$vuetify.breakpoint.xl
      }
    }
  }
</script>
