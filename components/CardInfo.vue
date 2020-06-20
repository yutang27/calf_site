<template>
  <v-card>
    <v-row>
      <v-col>
        <v-text-field
          label="speed"
        ></v-text-field>
      </v-col>

    </v-row>
    <v-row>
      <v-col>
        <v-text-field
          label="KP"
        ></v-text-field>
      </v-col>
      <v-col>
        <v-text-field
          label="KI"
        ></v-text-field>
      </v-col>
      <v-col>
        <v-text-field
          label="KD"
        ></v-text-field>
      </v-col>
    </v-row>
  </v-card>
</template>

<script>
  export default {
    name: "CardInfo"
  }
</script>
