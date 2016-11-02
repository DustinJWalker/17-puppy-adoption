<template lang="html">
  <div class="">

    <div class="nav">
      <div class="nav__container">
        <router-link to="/index" class="is-brand">Puppies</router-link>
        <router-link to="/index" class ="is-brand">All Puppies</router-link>
        <router-link to="/new" class="is-brand">Add a Puppy</router-link>
      </div>
    </div>

    <div class="sidebar"><p>Adopt a Pupper<p>
      <router-link class="sidebar__puppies-list"></router-link>
      <router-link class="sidebar__puppies-image"> </router-link>
      <router-link class="sidebar__puppies-name"></router-link>
    </div>









  </div>
</template>

<script>
export default {
  data() {
    return {
    };
  },

  methods: {

  },
};
</script>
