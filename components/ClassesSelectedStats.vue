<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="12" md="12" lg="8">
      <v-card>
        <v-card-title> Total Credits: {{ totalCredits }}</v-card-title>
        <v-card-title>Selected Classes:</v-card-title>
        <div class="text-center">
          <v-chip
            class="ma-2"
            v-for="clas in selectedClasses"
            :key="clas.crn"
            @click:close="$emit('class:delete', clas)"
            close
          >
            {{ clas.name }}{{ clas.credits }} {{ clas.crn }}
          </v-chip>
        </div>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
  export default {
    data() {
      return {}
    },
    props: {
      selectedClasses: { type: Array, default: [] },
    },
    computed: {
      totalCredits() {
        // +b to convert string to number.
        // +"03" =>> 3
        let credits = this.selectedClasses.reduce((a, b) => +b.credits + a, 0)
        if (isNaN(credits)) {
          return 'Unknown'
        } else {
          return credits
        }
      },
    },
  }
</script>
