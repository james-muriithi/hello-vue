<template>
  <li>
    <h2>{{ friend.name }}</h2>
    <button @click="toggleDetails">{{detailsAreVisisble ? 'Hide': 'Show'}}</button>
    <ul v-if="detailsAreVisisble">
      <li><strong>Phone: </strong> {{ friend.phone }}</li>
      <li><strong>Email: </strong> {{ friend.email }}</li>
    </ul>
  </li>
</template>

<script>
export default {
  props: [
      "friend"
  ],
  data() {
    return {
      detailsAreVisisble: false,
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisisble = !this.detailsAreVisisble;
    },
  },
};
</script>
