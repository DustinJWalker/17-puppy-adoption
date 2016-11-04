<template lang="html">
  <div class="">
    <h1>Found a Pupper?  We can help!</h1>
    <form @submit.prevent="saveForm">
      <label for="label">Name</label>
      <p class="control">
        <input class="input" type="text">
      </p>
      <label for="label">Age</label>
      <p class="control">
        <input class="input" type="text">
      </p>
      <label class="label">Sex</label>
      <p class="control">
        <span class="select">
            <select>
              <option>Male</option>
              <option>Female</option>
            </select>
          </span>
      </p>
      <label for="label">Color</label>
      <p class="control">
        <input class="input" type="text">
      </p>
      <label for="label">Breed</label>
      <p class="control">
        <input class="input" type="text">
      </p>
      <label for="label">Image Url</label>
      <p class="control">
        <input class="input" type="text">
      </p>
      <label class="label">Description</label>
      <p class="control">
        <textarea class="textarea" placeholder="Textarea"></textarea>
      </p>
      <p class="control">
        <button class="button is-outlined">Back</button>
        <button class="button is-primary">Submit</button>
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
      this.$emit('addPuppies', this.formValues);

    },
  },
};
</script>
