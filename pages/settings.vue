<template>
  <div>
    <v-btn to="/"><v-icon>mdi-home</v-icon>back home</v-btn>

    <template>
      <div class="text-center">

        <v-btn
          :loading="loading2"
          :disabled="loading2"
          color="success"
          @click="loader = 'loading2'"
        >
          Custom Loader
          <template v-slot:loader>
            <span>切换中...</span>
          </template>
        </v-btn>

      </div>
    </template>
  </div>
</template>

<script>
  export default {
    name: "settings",
   //  data: () => ({
   //    tab: null,
   //
   // }),
    data () {
      return {
        loader: null,
        loading2: false,
      }
    },
    watch: {
      loader () {
        const l = this.loader
        this[l] = !this[l]
        setTimeout(() => (this[l] = false), 3000)
        this.loader = null
      },
    },
  }
</script>

