<template>
  <v-container class="ma-5">

    <h1 class="pa-8 text-center">View Sugguestion </h1>
    <h4>Select view status</h4>
    <h4>View : {{ filter }}</h4>

    <v-btn class="bg-purple" @click="filterOpen()">open & Escalate</v-btn>
    <v-btn class="ma-2 bg-pink" @click="filterClose()">close</v-btn>

    <v-card v-for="(fb, n) in feedback" :key="n" class="pa-4 my-4 bg-purple-lighten-5">

      <v-container v-if="fb.status == filter">
        <h2>Ref ID : {{ fb.id }}</h2>
        <h3>Status : {{ fb.status }}</h3>
        <a>
          <b>Name : </b> {{ fb.fname }} {{ fb.lname }} <br />
          <b>email : </b> {{ fb.email }} <br />
          <b>suggegstion : </b> {{ fb.suggest }} <br>
          <b>Timestamp : </b> {{ fb.timestamp }} <br>
        </a>
        <v-btn class="bg-yellow ma-5" @click="dialog = true">Change status</v-btn>

        <!-- Dialog popup -->
        <v-dialog v-model="dialog" width="500" hight="500">
          <v-card>
            <v-card-title class=" grey lighten-2">
              ref ID : {{ rid }}
            </v-card-title>
            <v-divider></v-divider>
            <v-card-text>
              Change status
            </v-card-text>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn class="yellow" @click="changeStatus(escalate)">
                Escalate
              </v-btn>
              <v-btn class="black" @click="changeStatus(close)">
                Close
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-dialog>
      </v-container>

    </v-card>
  </v-container>


</template>

<script>
import { store_feedback } from "../stores/store_feedback";

export default {
  // Declare Vue file (View/Component) is named
  name: "SugView",

  // Declare local variables (scoped only this file)
  data: () => ({
    modelStore: store_feedback(),
    feedback: [],
    btn: [],
    filter: 'open',
    dialog: false,
    msg: '',
    rid: '',
    n: '0'
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
    },
    filterOpen() {
      this.filter = 'open'
    },
    filterClose() {
      this.filter = 'close'
    },
    changeStatus(status) {
      const data = {
        id: this.rid,
        status: status
      }
      this.modelStore.updateFeedback(data)
      this.dialog = false
    },
    getID(id) {
      this.rid = id;
    },
    increment(n) {
      this.n++;
    }
  },

  // In my understand this is like "Constructur method in java :)
  mounted() {
    this.QueryFeedback();

  },
};
</script>