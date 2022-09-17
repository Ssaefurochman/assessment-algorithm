<template>
  <v-app>
    <v-main>
      <v-container fluid>
        <v-row>
          <v-col cols="12">
            <CompareTriplets />
          </v-col>
          <v-col cols="12">
            <CheckPrime />
          </v-col>
          <v-col cols="12">
            <RemoveDuplicate />
          </v-col>
          <v-col cols="12">
            <ReverseWords />
          </v-col>
          <v-col cols="12">
            <FirstNoDuplicate />
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import CompareTriplets from './components/CompareTriplets.vue'
import CheckPrime from './components/CheckPrime.vue'
import RemoveDuplicate from './components/RemoveDuplicate.vue'
import ReverseWords from './components/ReverseWords.vue'
import FirstNoDuplicate from './components/FirstNoDuplicate.vue'

export default {
  name: 'App',

  components: {
    CompareTriplets,
    CheckPrime,
    RemoveDuplicate,
    ReverseWords,
    FirstNoDuplicate
},

  data: () => ({
    //
  })
}
</script>
