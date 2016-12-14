<template lang="html">
  <div class="">
    <h1 class="title">Found a Pupper?  We can help!</h1>
    <form @submit.prevent="saveForm">
      <label for="puppy-name"><strong>Name</strong</label>
      <p class="control">
        <input id="puppy-name" class="input" type="text" v-model="formValues.name">
      </p>
      <label for="puppy-age"><strong>Age</strong></label>
      <p class="control">
        <input id="puppy-age" class="input" type="text" v-model="formValues.age">
      </p>
      <label for="puppy-sex"><strong>Sex</strong></label>
      <p class="control">
        <span class="select">
            <select v-model="formValues.sex" id="puppy-sex">
              <option value="">Select Dropdown</option>
              <option>Male</option>
              <option>Female</option>
            </select>
          </span>
      </p>
      <label for="puppy-color"><strong>Color</strong></label>
      <p class="control">
        <input id="puppy-color" class="input" type="text" v-model="formValues.color">
      </p>
      <label for="puppy-breed"><strong>Breed</strong></label>
      <p class="control">
        <input id="puppy-breed" class="input" type="text" v-model="formValues.breed">
      </p>
      <label for="puppy-image"><strong>Image Url</strong></label>
      <p class="control">
        <input id="puppy-image" class="input" type="text" v-model="formValues.image_url">
      </p>
      <label class="puppy-description"><strong>Description</strong></label>
      <p class="control">
        <textarea id="puppy-description" v-model="formValues.description" class="textarea" placeholder="Textarea"></textarea>
      </p>
      <p class="control">
        <router-link :to="{ name: 'index' }" class="button is-primary is-outlined">Cancel</router-link>
        <button class="button is-info">Submit</button>
      </p>
    </form>
  </div>
</template>

<script>
const apiUrl =  'https://tiy-tn-class-api-fall-16.herokuapp.com/puppies/ryan';
export default {
  data() {
    return {
      formValues: {
        name: '',
        age: '',
        sex: '',
        color: '',
        breed: '',
        image_url: '',
        description: '',
      },
    };
  },

  methods: {
    saveForm() {
      this.$emit('addPuppy', this.formValues);

    },
  },
};
</script>
