<template>
  <div>
  <b-navbar toggleable="lg" type="dark" variant="info" sticky="top" class="mb-3">
    <b-navbar-brand href="#" v-on:click="changePage('home')">VisionListen</b-navbar-brand>

    <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

    <b-collapse id="nav-collapse" is-nav>

      <!-- Right aligned nav items -->
      <b-navbar-nav class="ml-auto">
        <b-nav-item href="#" v-on:click="changePage('uploader')">Upload Image</b-nav-item>

        <b-nav-item-dropdown right>
          <!-- Using 'button-content' slot -->
          <template v-slot:button-content>
            <em>User</em>
          </template>
          <b-dropdown-item href="#">Profile</b-dropdown-item>
          <b-dropdown-item href="#">Sign Out</b-dropdown-item>
        </b-nav-item-dropdown>
      </b-navbar-nav>
    </b-collapse>
  </b-navbar>
</div>
</template>

<script>
export default {
    data(){
        return {};
    },
    methods: {
        changePage: function(value){
            this.$emit('change-page', value);
        }
    }
}
</script>

<style>

</style>