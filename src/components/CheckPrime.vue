<template>
  <v-card>
    <v-card-title primary-title>
      Check Prime
    </v-card-title>
    <v-card-text>
      <v-form ref="testPrimeForm" lazy-validation>
        <v-row>
          <v-col cols="12">
            <v-text-field
              v-model="checkNumber"
              label="Enter a number"
              :rules="[
                v => !!v || 'Field is required',
                checkedNumberRule()
              ]"
            />
          </v-col>
        </v-row>
      </v-form>
      <v-row>
        <v-col cols="12">
          <v-text-field
            v-model="testResult"
            label="Result Prime Number"
            readonly
          />
        </v-col>
      </v-row>
    </v-card-text>
    <v-card-text>
      <v-btn color="error" @click="resetNumber" class="mr-1">Reset</v-btn>
      <v-btn color="success" @click="testPrimeNumber" class="ml-1">Test</v-btn>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  data () {
    return {
      checkNumber: null,
      testResult: null
    }
  },
  methods: {
    testPrimeNumber () {
      if (this.$refs.testPrimeForm.validate()) {
        this.testResult = null
        for (let i = 2; i < this.checkNumber; i++) {
          if (this.checkNumber % i === 0) {
            this.testResult = 'The number IS NOT a prime number (false)'
            break
          } else {
            this.testResult = 'The number IS a prime number (true)'
          }
        }
      }
    },
    resetNumber () {
      this.checkNumber = null
      this.testResult = null
    },
    checkedNumberRule () {
      return this.checkNumber > 1 || 'Number must be higher than 1'
    }
  }
}
</script>
