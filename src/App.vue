<template>
  <v-app>
    <v-content>
      <v-container>
        <Calculator />
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
import Calculator from '@/components/Calculator.vue'

export default {
  name: 'App',
  components: {
    Calculator
  }
};
</script>
