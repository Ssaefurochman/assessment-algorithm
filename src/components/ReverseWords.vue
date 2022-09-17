<template>
  <v-card>
    <v-card-title primary-title>
      Reverse String
    </v-card-title>
    <v-card-text>
      <v-form ref="reverseStringForm" lazy-validation>
        <v-row>
          <v-col cols="12">
            <v-text-field
              v-model="inputString"
              label="Enter a sentences"
              :rules="[
                v => !!v || 'Field is required'
              ]"
            />
          </v-col>
        </v-row>
      </v-form>
      <v-row>
        <v-col cols="12">
          <v-text-field
            v-model="reversedString"
            label="Reversed String"
            readonly
          />
        </v-col>
      </v-row>
    </v-card-text>
    <v-card-text>
      <v-btn color="error" @click="resetState" class="mr-1">Reset</v-btn>
      <v-btn color="success" @click="reverseString" class="ml-1">Reverse</v-btn>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  data () {
    return {
      inputString: null,
      reversedString: null
    }
  },
  methods: {
    reverseString () {
      if (this.$refs.reverseStringForm.validate()) {
        const sentenceSplit = this.inputString.split(' ')
        const wordSplit = sentenceSplit.map((v) => {
          const charSplit = v.split('')
          return charSplit.reverse().join('')
        })
        this.reversedString = wordSplit.join(' ')
      }
    },
    resetState () {
      this.inputString = null
      this.reversedString = null
    }
  }
}
</script>
