<template>
  <v-app>
    <v-main>
      
      <router-view/>
    </v-main>
  </v-app>
</template>

<script>
import { store_feedback } from "/src/stores/store_feedback";

export default {
  name: 'App',
  
  // Declare local variables (scoped only this file)
  data: () => ({
    modelStore: store_feedback(),
  }),

// Declare method/function
  methods: {
    QueryFeedback() {
      this.modelStore.getQueryFeedback();
    }
  },

  // In my understand this is like "Constructur method in java :)
  mounted() {
    this.QueryFeedback();
    
  },
  
}
</script>
