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

          <nav class="level">
            <div class="level-item">
            <p class="control has-addons">
              <h2 class="title">Luna</h2>
              <button class="button" @click="updatePuppy">
                <i class="fa fa-paw"></i>
                I'm Adopted
              </button></p>
            </nav>
            <div class="columns">
              <div class="is-columns is-offset">
                <div class="card">
                  <div class="card-image">
                    <figure class="is-square">
                      <img src="http://placehold.it/480x480" alt="">
                    </figure>
                  </div>
                </div>
              </div>
            </div>
        <div class="level-item has-text-centered">
          <p class="heading">Age</p>
          <p class="title">2</p>
        </div>
        <div class="level-item has-text-centered">
          <p class="heading">Breed</p>
          <p class="title">Hound</p>
        </div>
        <div class="level-item has-text-centered">
          <p class="heading">Color</p>
          <p class="title">Tri-Color</p>
        </div>
        <div class="level-item has-text-centered">
          <p class="heading">Sex</p>
          <p class="title">Female</p>
        </div>
      </div>

      <div class="content">
        <h1 class="title">About Me</h1>
        <p>They're good dogs Brandt!!</p>
      </div>
  </div>

</template>

<script>
export default {
  data() {
    return {
      puppy: '',
      id: '',
      props: ['apiUrl'],
    };
  },

  mounted(){
    this.loadData();
  },

  methods: {
    getData(){
      fetch(`${this.apiUrl}/${this.$route.path.id}`)
      .then((r) => r.json())
      .then((puppies) =>{
        this.puppies = puppies;
      });
    },

    updatePuppy() {
      if(confirm('Adopt this Pupper?')) {
        this.$emit()
      }
    }

  },
};
</script>
