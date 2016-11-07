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
                    <img :src="puppy.image_url" alt="" />
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
    </div>

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

  mounted(){
    this.loadData();
  },

  methods: {
    loadData(){
      fetch(`${this.apiUrl}/${this.$route.params.id}`)
      .then((r) => r.json())
      .then((puppy) =>{
        this.puppy = puppy;
      })
      .catch(() => {
        this.$router.push({
          name: 'index'
        });
      });
    },

    removePuppy() {
      if(confirm('Are you sure?')){
        this.$emit('removePuppy', this.puppy);
      }
    },

    adoptPuppy() {
      this.$router.push({
        name: 'index'
      });
      this.$emit('updatePuppy', this.puppy.id, { adopted: true });
    },

  },
};
</script>
