<template>
<v-card
    class="mx-auto"
    max-width="800"
    tile
  >
    <v-list-item v-for="item in items" :key='item.id'>
      <v-list-item-content>
        <v-list-item-title><h3>{{item.type}}</h3></v-list-item-title>
        <v-list-item-subtitle>
          <h4>Date</h4>{{item.date}}
        </v-list-item-subtitle>
        <v-list-item-subtitle>
         <h4>Duration</h4> {{item.time}} minutes
        </v-list-item-subtitle>
        <v-list-item-subtitle>
          <h4>Workout Units</h4>{{item.amount}} {{item.unit}}
        </v-list-item-subtitle>
      </v-list-item-content>
    </v-list-item>

  </v-card>
</template>

<script>
export default {
  name: 'tracker',
  props: {
    items: Array
  }
}
</script>

<style>

</style>
