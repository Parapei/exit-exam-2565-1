<template>
  <h1 class="pa-8 text-center">Sugguestion center</h1>
  <h2 class="pa-3 text-center">Select option</h2>
  <v-row class="pa-5">
    <v-col class="text-center ma-2 pa-2 height-100">
        <v-card class="pa-5 bg-blue-lighten-5" height="600" to="/write">
          <h2 class="pa-5">Write Sugguestion</h2>
        </v-card>
    </v-col>
    <v-col class="text-center  ma-2 pa-2">
      <v-card class="pa-5 bg-red-lighten-5" height="600" to="/suggestion">
        <h2 class="pa-5">view all sugguestion for admin</h2>
      </v-card>
    </v-col>
  </v-row>

</template>