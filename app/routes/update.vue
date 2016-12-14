<template lang="html">
  <div class="">
    <h1 class="title">Update Puppy Info</h1>
    <form @submit.prevent="savePuppy">
      <label for="puppy-name"><strong>Name</strong></label>
      <p class="control">
        <input class="input" type="text" v-model="formValues.name" id="puppy-name">
      </p>
      <label for="puppy-age"><strong>Age</strong></label>
      <p class="control">
        <input class="input" type="text" v-model="formValues.age" id="puppy-age">
      </p>
      <label for="puppy-sex"><strong>Sex</strong></label>
      <p class="control">
        <span class="select">
          <select v-model="formValues.sex" id="puppy-sex">
            <option>Select Dropdown</option>
            <option>Male</option>
            <option>Female</option>

          </select>
        </span>
      </p>

      <label for="puppy-color">Color</label>
      <p class="control">
        <input class="input" type="text" v-model="formValues.color" id="puppy-color">
      </p>
      <label for="puppy-breed">Breed</label>
      <p class="control">
        <input class="input" type="text" v-model="formValues.breed" id="puppy-breed">
      </p>
      <label for="puppy-image">Image Url</label>
      <p class="control">
        <input class="input" type="text" v-model="formValues.image_url" id="puppy-image">
      </p>
      <label for="puppy-breed">Description</label>
      <p class="control">
        <input class="input" type="text" v-model="formValues.description" id="puppy-description">
      </p>
      <p class="control">
        <router-link :to="{ name: 'index' }" class="button is-primary is-outlined">Cancel</router-link>
        <button class="button is-info">Submit</button>
      </p>





    </form>
  </div>
</template>

<script>
export default {
  props: ['findPuppy'],
  data() {
    return {
      puppy: {},
      formValues: {},
    };
  },

  mounted() {
    this.getData();
  },

  methods: {
    getData() {
      this.findPuppy(this.$route.params.id)
      .then((puppy) => {
        this.formValues = { ...puppy };
        this.puppy = puppy;
      });
    },
    savePuppy() {
      this.$emit('updatePuppy', this.puppy.id, this.formValues);
      this.$router.push({ name: 'index'});
    },
  },
};
</script>
