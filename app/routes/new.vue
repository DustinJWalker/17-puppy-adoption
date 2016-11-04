<template lang="html">
  <div class="">

    <nav class="nav">
      <div class="nav-left">
        <router-link to="{ name: 'index' }" class="nav-item is-brand">Puppies</router-link>
      </div>
      <div class="nav-right">
        <router-link to="{ name: 'index' }" class="nav-item is-brand">All Puppies</router-link>
        <router-link to="{ name: 'new' }" class="nav-item is-brand">Add Puppy</router-link>
      </div>
    </nav>

  <div class="section">
    <div class="container ">
      <div class="columns">
        <div class="column is-4">
          <nav class="panel">
            <p class="panel-heading">
              Adopt a Pupper
            </p>
            <div class="panel-block">
              <div class="media">
                <div class="media-left">
                  <p class="image is-64x64">
                    <img src="http://placehold.it/128x128" alt="" />
                  </p>
                </div>

                <div class="media-right">
                  <h2>Pupper Name</h2>
                   <a class="is-active" href="#">Read more</a>
                </div>
              </div>
            </div>

          </nav>
        </div>
      </div>
      <h1>Found a Pupper?  We can help!</h1>
      <form action="">
        <label for="label">Name</label>
          <p class="control">
            <input class="input" type="text">
          </p>
        <label for="label">Age</label>
          <p class="control">
            <input type="input" type="text">
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
  </div>

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
      }
    };
  },

  methods: {

  },
};
</script>
