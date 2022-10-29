<template>
    <h1 class="pa-8 text-center">Write your Sugguestion</h1>
    <v-container class="bg-blue-lighten-5 ma-5 ">
      <h3 >First Name</h3>
      <v-text-field 
          v-model="fname"
          label="Enter firstName"
      ></v-text-field>
      <h3>Last Name</h3>
      <v-text-field 
          v-model="lname"
          label="Enter lastname"
      ></v-text-field>
      <h3>E-mail</h3>
      <v-text-field 
          v-model="email"
          label="Enter E-mail"
      ></v-text-field>
      <h3>Sugguestion</h3>
      <v-text-field 
          v-model="sug"
          label="Enter Sugguestion"
      ></v-text-field>
      <v-btn color="blue" @click="send()">
          send
        </v-btn>
  </v-container>
</template>


<script>
import { store_feedback  } from "../stores/store_feedback";
import { useRouter } from 'vue-router'

export default {
  name: "StudentSignup",

  data: () => ({
    modelStore: store_feedback(),
    router: useRouter(),
    fname: '',
    lname: '',
    email: '',
    sug: '',
  }),

  methods: {
    send() {
        const data = {
          fname: this.fname,
          lname: this.lname,
          email: this.email,
          suggest: this.sug,
          timestamp: new Date().toLocaleString(),
          status: 'open',
        }
        console.log(data);
        this.modelStore.addSug(data)
        this.router.push('/')
      
    },
  },
};
</script>