<template lang="html">
  <div class="">

    <nav class="nav">
      <div class="nav__left">
        <router-link to="/" class="nav-item is-brand">Puppies</router-link>
      </div>
      <div class="nav__right">
        <router-link to="/" class="nav-item is-brand">All Puppies</router-link>
        <router-link to="/new" class="nav-item is-brand">Add Puppy</router-link>
      </div>
    </nav>

  <div class="section">
    <div class="container">
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

                </div>

              </div>
            </div>
          </nav>
        </div>
      </div>
    </div>
  </div>














  </div>
</template>

<script>
const apiUrl =  'https://tiy-tn-class-api-fall-16.herokuapp.com/puppies/ryan';
export default {
  data() {
    return {
      apiUrl,
      puppies: [],
      path: window.location.pathname,
    };
  },

  methods: {
    getData() {
      fetch(apiUrl)
      .then((r) => r.json())
      .then((puppies) => {
        this.puppies = puppies;
      });
    },

  },
};
</script>
