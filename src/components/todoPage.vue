<template>
  <v-layout row justify-center>
    <v-dialog v-model="addDialog" persistent max-width="500">
      <v-card class="h-75">
        <v-sheet width="400" class="mx-auto">

          <v-form ref="form">
            <v-text-field
                v-model="name"
                :counter="10"
                :rules="nameRules"
                label="Name"
                required
            ></v-text-field>

            <v-select
                v-model="select"
                :items="items"
                :rules="[v => !!v || 'Item is required']"
                label="Item"
                required
            ></v-select>

            <v-checkbox
                v-model="checkbox"
                :rules="[v => !!v || 'You must agree to continue!']"
                label="Do you agree?"
                required
            ></v-checkbox>
          </v-form>
        </v-sheet>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="green darken-1" flat
                 variant="outlined"
                 @click="addDialog=false">Add
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-layout>
</template>


<script setup lang="ts">

import {useCounterStore} from '@/stores/counter'
import {storeToRefs} from 'pinia'
import {isRef} from "vue";


const store = useCounterStore()

const {addDialog} = storeToRefs(store)

console.log(isRef(addDialog))
</script>

<style scoped>


</style>

