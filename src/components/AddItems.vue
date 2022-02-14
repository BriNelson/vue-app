<template>
  <v-form @submit.prevent='handleSubmit'>
    <v-container>
      <v-row>
        <v-col
          cols="12"
          md="4"
        >
          <v-text-field
            v-model="item.type"
            label="Exercise Type"
            required
          ></v-text-field>
        </v-col>
        <v-col
          cols="12"
          md="4"
        >
          <v-text-field
            v-model="item.time"
            label="Exercise Duration"
          ></v-text-field>
        </v-col>

        <v-col
          cols="12"
          md="4"
        >
          <v-menu
        ref="menu"
        v-model="menu"
        :close-on-content-click="false"
        :return-value.sync="date"
        transition="scale-transition"
        offset-y
        min-width="auto"
      >
        <template v-slot:activator="{ on, attrs }">
          <v-text-field
            v-model="item.date"
            label="Date"
            prepend-icon="mdi-calendar"
            readonly
            v-bind="attrs"
            v-on="on"
          ></v-text-field>
        </template>
        <v-date-picker
          v-model="item.date"
          no-title
          scrollable
        >
          <v-spacer></v-spacer>
          <v-btn
            text
            color="primary"
            @click="menu = false"
          >
            Cancel
          </v-btn>
          <v-btn
            text
            color="primary"
            @click="$refs.menu.save(item.date)"
          >
            OK
          </v-btn>
        </v-date-picker>
      </v-menu>
      {{item.date}}
        </v-col>
 </v-row>
  <v-row>
        <v-col
          cols="12"
          md="4"
        >
          <v-select
          :items="items"
          v-model="item.unit"
          label="Workout Units"
        ></v-select>
        </v-col>
        <v-col
          cols="12"
          md="4"
        >
<v-text-field
            label="Amount"
            v-model="item.amount"
            required
          ></v-text-field>
        </v-col>
        <v-col
          cols="12"
          md="4"
        >
            <v-btn
      class="mr-4"
      color="primary"
      @click="handleSubmit"
    >
      Add Item
    </v-btn>
        </v-col>

      </v-row>
    </v-container>
  </v-form>
</template>

<script>
export default {
  name: 'add-items',
  data () {
    return {
      date: (new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10),
      menu: false,
      item: {
        type: '',
        date: '',
        time: 0,
        unit: '',
        amount: 0
      },
      items: ['Reps', 'Sets', 'Laps', 'Weight', 'steps']
    }
  },
  methods: {
    handleSubmit: function () {
      this.$emit('add:item', this.item)
      this.item = {
        type: '',
        date: '',
        time: 0,
        unit: '',
        amount: 0
      }
      console.log('Submit')
    }
  }
}
</script>

<style>

</style>
