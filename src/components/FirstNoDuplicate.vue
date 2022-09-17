<template>
  <v-card>
    <v-card-title primary-title>
      First non duplicate
    </v-card-title>
    <v-card-text>
      <v-form ref="firstNoDuplicateForm" lazy-validation>
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
            v-model="firstNoDuplicate"
            label="First non duplicate"
            readonly
          />
        </v-col>
      </v-row>
    </v-card-text>
    <v-card-text>
      <v-btn color="error" @click="resetState" class="mr-1">Reset</v-btn>
      <v-btn color="success" @click="getFirstNonDuplicate" class="ml-1">Test</v-btn>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  data () {
    return {
      inputString: null,
      firstNoDuplicate: null
    }
  },
  methods: {
    getFirstNonDuplicate () {
      if (this.$refs.firstNoDuplicateForm.validate()) {
        const result = this.inputString.split('').filter((character, index, obj) => {
          return obj.indexOf(character) === obj.lastIndexOf(character)
        }).shift()
        this.firstNoDuplicate = result
      }
    },
    resetState () {
      this.inputString = null
      this.firstNoDuplicate = null
    }
  }
}
</script>
