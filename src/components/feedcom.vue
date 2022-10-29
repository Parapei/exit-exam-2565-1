<template>
    <h2>Ref ID : {{ fb.id }}</h2>
    <h3>Status : {{ fb.status }}</h3>
    <a>
        <b>Name : </b> {{ fb.fname }} {{ fb.lname }} <br />
        <b>email : </b> {{ fb.email }} <br />
        <b>suggegstion : </b> {{ fb.suggest }} <br>
        <b>Timestamp : </b> {{ fb.timestamp }} <br>
    </a>
    <v-btn class="bg-yellow ma-5" @click="dialog = true">Status</v-btn>
</template>

<script>
import { store_feedback } from "../stores/store_feedback";

export default {
  // Declare Vue file (View/Component) is named
  name: "feedcom",

  // Declare local variables (scoped only this file)
  data: () => ({
    modelStore: store_feedback(),
    feedback: [],
    fb: {},
  }),

  // Declare computed for get reactive data/variables
  // In this case, use to get data from pinia
  computed: {
    getFeedbackList() {
      return this.modelStore.getFeedback;
    },
  },

  // Declare method/function
  methods: {
    QueryFeedback() {
      this.modelStore.getQueryFeedback();
      this.feedback = this.getFeedbackList;
      this.fb = this.feedback[this.n];
    },
  },

  // In my understand this is like "Constructur method in java :)
  mounted() {
    this.QueryFeedback();
    
  },
  
}
