<template lang="html">
  <div class="">
  <h1 class="title has-text-centered">{{ puppy.name }}
    <a class="button is-primary" @click="update" v-if="!puppy.adopted">
      <span class="icon is-small">
        <i class="fa fa-paw" aria-hidded="true">
      </span>
      <span>Adopt Me</span>
    </a>
    <a class="button is-success" v-if="puppy.adopted">
      <span class="icon is-small" aria-hidden="true">
        <i class="fa fa-paw" aria-hidden="true">
      </span>
      <span>I'm Adopted</span>
    </a>
  </h1>
  <div class="columns">
    <div class="column is-half is-offset-one-quarter">
      <figure class="image">
        <img :src="puppy.image_url" alt="">
      </figure>
    </div>
  </div>
  <nav class="level">
    <div class="level-item has-text-centered">
      <p class="heading">Age</p>
      <p class="title">{{ puppy.age }}</p>
    </div>
    <div class="level-item has-text-centered">
      <p class="heading">Breed</p>
      <p class="title">{{ puppy.breed }}</p>
    </div>
    <div class="level-item has-text-centered">
      <p class="heading">Color</p>
      <p class="title">{{ puppy.color }}</p>
    </div>
    <div class="level-item has-text-centered">
      <p class="heading">Sex</p>
      <p class="title">{{ puppy.sex }}</p>
    </div>
  </nav>

  <div class="content has-text-centered">
    <h3>About Me</h3>
    <p>{{ puppy.description }}</p>
  </div>

  <h1 class="title has-text-centered">
    <a class="button is-primary" @click="removePuppy">Remove Puppy</a>
    <router-link class="button is-primary" :to="{ name: 'update', params: { id: puppy.id }}">Edit Listing</router-link>
  </h1>




    </div>
  </template>
  <script>
  export default {
    props: ['findPuppy', 'puppies'],
    data() {
      return {
        puppy: {},
        id: this.$route.params.id,
      };
    },

    mounted() {
      this.getData();
    },

    watch: {
      '$route': 'getData',
      'puppies': 'getData',
    },

    methods: {
      getData() {
        this.findPuppy(this.$route.params.id)
        .then((puppy) => {
          this.puppy = puppy;
        });
      },

      update() {
        this.$emit('updatePuppy', this.puppy.id, { adopted: true});
      },

      removePuppy() {
        if (confirm('Are you sure?')) {
          this.$emit('removePuppy', this.puppy);
        }
      },
    },
  };
  </script>
