<template>
  <li>
    <h2>{{ friend.name }} {{friend.isFavorite ? '(Favorite)':''}}</h2>
    <button @click="toggleFavorite" class="mr-2">Toggle favorite</button>
    <button @click="toggleDetails" class="mr-2">{{detailsAreVisisble ? 'Hide': 'Show'}}</button>
    <button @click="$emit('delete', friend.id)">Delete</button>
    <ul v-if="detailsAreVisisble">
      <li><strong>Phone: </strong> {{ friend.phone }}</li>
      <li><strong>Email: </strong> {{ friend.email }}</li>
    </ul>
  </li>
</template>

<script>
export default {
  emits: ['delete', 'toggle-favorite'],
  props: {
    friend: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      detailsAreVisisble: false,
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisisble = !this.detailsAreVisisble;
    },
    toggleFavorite(){
      this.$emit('toggle-favorite', this.friend.id)
    }
  },
};
</script>

<style>
.mr-2{
  margin-right: 8px;
}
</style>