<template>
  <v-app>
    <v-main>
      <AddItems @add:item='addItem' />
<Tracker :items='exerciseItems'></Tracker>
     </v-main>
  </v-app>
</template>

<script>
import Tracker from './components/Tracker.vue'
import AddItems from './components/AddItems.vue'

export default {
  name: 'App',
  components: {
    Tracker,
    AddItems
  },

  data () {
    return {
      exerciseItems: [
        {
          id: 1,
          type: 'running',
          date: '',
          time: 25,
          units: 'reps'
        },
        {
          id: 1,
          type: 'running',
          date: '',
          time: 25,
          units: 'reps'
        },
        {
          id: 1,
          type: 'running',
          date: '',
          time: 25,
          units: 'sets'
        }
      ]
    }
  },
  methods: {
    addItem (item) {
      this.exerciseItems = [...this.exerciseItems, item]
    }
  }
}
</script>
