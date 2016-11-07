<template lang="html">
  <div class="">

  <div class="section">
    <div class="columns">
      <div class="column is-half">

      <div class="level">
        <div class="level-item">
          <h2 class="title">{{ puppy.name }}</h2>
          <template v-if="puppy.adopted">
            <button class="button" @click="removePuppy">
              <i class="fa fa-paw"></i>
              I'm Adopted
            </button>
          </template>
          <template v-else>
            <button class="button is-primary" @click="adopt">
              <i class="fa fa-paw"></i>
              Adopt Me!
            </button>
          </template>
        </div>
      </div>
        <div class="columns">
          <div class="is-columns is-offset">
            <div class="card">
              <div class="card-image">
                <figure class="is-square">
                  <img :src="puppy.image_url" alt="">
                </figure>
              </div>
            </div>
          </div>
        </div>
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
      </div>

      <div class="content">
        <h1 class="title">About Me</h1>
        <p class="subtitle">{{ puppy.description }}</p>
      </div>
    </div>

    </div>
  </template>
  <script>
  export default {
    props: ['apiUrl'],
    data() {
      return {
        puppy: '',
        id: this.$route.params.id,
        puppy: {},
        props: ['apiUrl'],
      };
    },

    mounted() {
      this.loadData();
    },

    methods: {
      loadData() {
        fetch(`${this.apiUrl}/${this.$route.params.id}`)
        .then((r) => r.json())
        .then((puppy) => {
          this.puppy = puppy;
        })
        .catch(() => {
          this.$router.push({
            name: 'index'
          });
        });
      },

      removePuppy() {
        if (confirm('Are you sure?')) {
          this.$emit('removePuppy', this.puppy);
        }
      },

      adoptPuppy() {
        this.$router.push({
          name: 'index'
        });
        this.$emit('updatePuppy', this.puppy.id, {
          adopted: true
        });
      },

    },
  };
  </script>
