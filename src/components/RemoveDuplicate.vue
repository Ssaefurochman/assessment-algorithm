<template>
  <v-card>
    <v-card-title primary-title>
      Remove Duplicate
    </v-card-title>
    <v-card-text>
      <v-row>
        <v-col cols="12">
          <v-form ref="duplicateForm" lazy-validation>
            <v-text-field
              v-model="inputArray"
              label="Input Array"
              :rules="[
                v => v && v.length > 0 || 'Field is required'
              ]"
              readonly
            />
          </v-form>
        </v-col>
        <v-col cols="12" class="mb-2">
          <div align="right">
            <v-btn color="primary" @click="randomArray">generate array</v-btn>
          </div>
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="12">
          <v-text-field
            v-model="resultArray"
            label="Result Array"
            readonly
          />
        </v-col>
      </v-row>
    </v-card-text>
    <v-card-text>
      <v-btn color="error" @click="resetArray" class="mr-1">Reset</v-btn>
      <v-btn color="success" @click="removeDuplicate" class="ml-1">Remove Duplicate</v-btn>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  data () {
    return {
      inputArray: [],
      resultArray: []
    }
  },
  methods: {
    randomArray () {
      this.inputArray = Array.from({ length: 20 }, () => Math.floor(Math.random() * 10))
    },
    removeDuplicate () {
      if (this.$refs.duplicateForm.validate()) {
        this.resultArray = [...new Set(this.inputArray)]
      }
    },
    resetArray () {
      this.inputArray = []
      this.resultArray = []
    }
  }
}
</script>
