<template>
  <div>
    <PetsTable
      species="dogs"
      :pets="dogs"
    />
  </div>
</template>

<script>
import { mapState } from 'vuex'
import PetsTable from '../components/PetsTable.vue'

export default {
  components: {
    PetsTable
  },
  data () {
    return {}
  },
  computed: {
    ...mapState([
      'dogs'
    ])
  }
}
</script>

<style scoped>
  .b-table {
    font-size: 20px;
  }
</style>
