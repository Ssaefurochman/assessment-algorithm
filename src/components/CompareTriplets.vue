<template>
  <v-card>
    <v-card-title primary-title>
      Compare the triplets
    </v-card-title>
    <v-card-text>
      <v-form ref="compareForm" lazy-validation>
        <v-row>
          <v-col cols="12">
            First Array
          </v-col>
          <v-col cols="4">
            <v-text-field
              v-model="firstArray[0]"
              label="Value 1"
              :rules="[
                v => !!v || 'Field is required',
                v => /^\d+$/.test(v) || 'Field must be a number'
              ]"
            />
          </v-col>
          <v-col cols="4">
            <v-text-field
              v-model="firstArray[1]"
              label="Value 2"
              :rules="[
                v => !!v || 'Field is required',
                v => /^\d+$/.test(v) || 'Field must be a number'
              ]"
            />
          </v-col>
          <v-col cols="4">
            <v-text-field
              v-model="firstArray[2]"
              label="Value 3"
              :rules="[
                v => !!v || 'Field is required',
                v => /^\d+$/.test(v) || 'Field must be a number'
              ]"
            />
          </v-col>
        </v-row>
        <v-row>
          <v-col cols="12">
            Second Array
          </v-col>
          <v-col cols="4">
            <v-text-field
              v-model="secondArray[0]"
              label="Value 1"
              :rules="[
                v => !!v || 'Field is required',
                v => /^\d+$/.test(v) || 'Field must be a number'
              ]"
            />
          </v-col>
          <v-col cols="4">
            <v-text-field
              v-model="secondArray[1]"
              label="Value 2"
              :rules="[
                v => !!v || 'Field is required',
                v => /^\d+$/.test(v) || 'Field must be a number'
              ]"
            />
          </v-col>
          <v-col cols="4">
            <v-text-field
              v-model="secondArray[2]"
              label="Value 3"
              :rules="[
                v => !!v || 'Field is required',
                v => /^\d+$/.test(v) || 'Field must be a number'
              ]"
            />
          </v-col>
        </v-row>
      </v-form>
      <v-row>
        <v-col cols="12">
          <v-text-field
            name="compareResult"
            v-model="compareResult"
            label="Comparation Result"
            readonly
          />
        </v-col>
      </v-row>
    </v-card-text>
    <v-card-text>
      <v-btn color="error" @click="resetArray" class="mr-1">Reset</v-btn>
      <v-btn color="primary" @click="randomizeArray" class="mr-1">Randomize</v-btn>
      <v-btn color="success" @click="compareArray" class="ml-1">Compare</v-btn>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  data () {
    return {
      firstArray: [],
      secondArray: [],
      compareResult: []
    }
  },
  methods: {
    randomizeArray () {
      this.resetArray()
      this.firstArray = Array.from({ length: 3 }, () => Math.floor(Math.random() * 100))
      this.secondArray = Array.from({ length: 3 }, () => Math.floor(Math.random() * 100))
    },
    compareArray () {
      if (this.$refs.compareForm.validate()) {
        this.compareResult = []
        for (let i = 0; i < this.firstArray.length; i++) {
          for (let j = 0; j < this.secondArray.length; j++) {
            if (i === j) {
              if (this.firstArray[i] !== this.secondArray[j]) {
                this.compareResult.push(1)
              }
            }
          }
        }
      }
    },
    resetArray () {
      this.firstArray = []
      this.secondArray = []
      this.compareResult = []
    }
  }
}
</script>
