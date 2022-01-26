<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
    <div class="container-fluid">
      <div
        class="collapse navbar-collapse justify-content-center"
        id="navbarNav"
      >
        <ul class="navbar-nav">
          <li @click="onNav(1)" class="nav-item">
            <a class="nav-link active" aria-current="page" href="#">Home</a>
          </li>
          <li @click="onNav(2)" class="nav-item">
            <a class="nav-link" href="#">Cart</a>
          </li>
          <li @click="onNav(3)" class="nav-item">
            <a class="nav-link" href="#">Pricing</a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: "Nav",
  methods: {
    onNav(id) {
      this.$emit("onNav", id);
    },
  },
  props: {
    nav: {
      required: true,
    },
  },
};
</script>

<style lang="scss"></style>
