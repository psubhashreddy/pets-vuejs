<template>
  <div class="home">
    <h1>Adopt a new best friend.</h1>
    <h2>{{ animalsCount }}</h2>
    <button @click="togglePetForm" class="btn btn-primary">Add New Pet</button>
    <b-form @submit.prevent="handleSubmit" v-if="showPetForm">

      <b-form-group id="input-name" label="Enter Pets Name:" label-for="pet-name">
        <b-form-input
          id="pet-name"
          type="text"
          v-model="formData.name"
          required
          placeholder="Enter pets name"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-species" label="Species:" label-for="pet-species">
        <b-form-select
          id="pet-species"
          v-model="formData.species"
          :options="['Cats', 'Dogs']"
          required
        ></b-form-select>
      </b-form-group>

      <b-form-group id="input-age" label="Enter Pets Age:" label-for="pet-age">
        <b-form-input
          id="pet-age"
          type="number"
          v-model="formData.age"
          required
          placeholder="Enter pets age"
        ></b-form-input>
      </b-form-group>

      <b-button type="submit" variant="primary">Submit</b-button>
      <b-button type="reset" variant="danger">Reset</b-button>
    </b-form>
  </div>
</template>

<script>
import { mapActions, mapGetters } from 'vuex'

export default {
  name: 'home',
  data () {
    return {
      showPetForm: false,
      formData: {
        name: '',
        age: 0,
        species: null
      }
    }
  },
  computed: {
    ...mapGetters([
      'animalsCount'
    ])
  },
  methods: {
    ...mapActions([
      'addPet'
    ]),
    togglePetForm () {
      this.showPetForm = !this.showPetForm
    },
    handleSubmit () {
      const { species, age, name } = this.formData
      const payload = {
        species,
        pet: {
          name,
          age
        }
      }
      this.addPet(payload)

      this.formData = {
        name: '',
        age: 0,
        species: null
      }
    }
  }
}
</script>
