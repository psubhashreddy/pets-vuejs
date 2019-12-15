<template>
  <div>
    <PetsTable
      species="cats"
      :pets="cats"
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
      'cats'
    ])
  }
}
</script>

<style scoped>
  .b-table {
    font-size: 20px;
  }
</style>
