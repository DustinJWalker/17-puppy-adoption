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
    <div class="container">
      <div class="columns">
        <div class="column is-4">
          <div class="panel">
            <p class="panel-heading">
              Adopt a Pupper
            </p>
            <div class="panel-block is-active" v-for="puppy in puppies">
              <div class="media">
                <div class="media-left">
                  <p class="image is-64x64">
                    <img :src="puppy.image_url" alt="" />
                  </p>
                </div>

                <div class="media-right">
                  <h2 class="subtitle">{{ puppy.name }}</h2>
                   <router-link class="router-link" :to="{ name: 'detail', params: {id:puppy.id} }">
                     Read More
                   </router-link>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="column">
          <div class="is-relative">
            <transition name="fade">
              <router-view
              :puppies="puppies"
              :api-url="apiUrl"
              @addPuppy="addPuppy"
              @removePuppy="removePuppy"
              @updatePuppy="updatePuppy">
            </router-view>
          </transition>
      </div>
    </div>
  </div>
</div>
</template>
<script>

import IndexPage from './index.vue'

const apiUrl =  'https://tiy-tn-class-api-fall-16.herokuapp.com/puppies/Dustin';
export default {
  data() {
    return {
      apiUrl,
      puppies: [],
      path: window.location.pathname,
    };
  },

  mounted() {
    this.getData();
  },

  methods: {
    getData() {
      fetch(apiUrl)
      .then((r) => r.json())
      .then((puppies) => {
        this.puppies = puppies;
      });
    },
    addPuppy(input) {
      fetch(apiUrl, {
        method: 'POST',
        headers: { 'Content-Type': 'application/json'},
        body: JSON.stringify(input),
      })

      .then((r) => r.json())
      .then((puppies)=> {
        this.puppies = [puppies,...this.puppies];
        this.$router.push({ name: 'index'});
      });
    },
    removePuppy(puppies) {
      fetch(`${apiUrl}/${puppies.id}`, {
        method: 'DELETE',
      })


      .then(() => {
        this.puppies = this.puppies.filter((old) => old.id !== lunchSpot.id);
        this.$router.push({ name: 'index' });
      });
    },
    updatePuppy(id, formValues) {
      fetch(`${apiUrl}/${id}`, {
        method: 'POST',
        headers: { 'Content-Type': 'application/json'},
        body: JSON.stringify(input),
      })
      .then((r) => r.json())
      .then((puppies) => {
        this.puppies = [puppies,...this.puppies];
      });
    },

  },
};
</script>
