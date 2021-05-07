<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <client-only>
        <matrix />
      </client-only>
    </v-col>
  </v-row>
</template>

<script>
import Matrix from '../components/Matrix.vue'
export default {
  components: { Matrix },
}
</script>
