<template>
  <header><h1>My Friends</h1></header>
  <ul>
    <new-friend @add-friend="addContact"></new-friend>

    <friend-contact
      v-for="friend in friends"
      :friend="friend"
      :key="friend.id"
      @toggle-favorite="toggleFavoriteStatus"
      @delete="deleteContact"
    ></friend-contact>
  </ul>
</template>
<script>
import FriendContact from "./components/FriendContact.vue";
import NewFriend from "./components/NewFriend.vue";

export default {
  components: { FriendContact, NewFriend },
  data() {
    return {
      friends: [
        {
          id: 1,
          name: "xx xx",
          phone: "123",
          email: "s@w.com",
          isFavorite: false,
        },
        {
          id: 2,
          name: "yy yy",
          phone: "324",
          email: "z@e.com",
          isFavorite: true,
        },
      ],
    };
  },
  methods: {
    toggleFavoriteStatus(id) {
      const f = this.friends.find((friend) => friend.id == id);
      f.isFavorite = !f.isFavorite;
    },
    addContact(name, phone, email){
      const newFriendContact = {
        id: new Date().toISOString(),
        name,
        phone,
        email,
        isFavorite: false
      }

      this.friends.unshift(newFriendContact);

    },
    deleteContact(id){
      this.friends = this.friends.filter(friend => friend.id !== id)
    }
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: "Jost", sans-serif;
}

body {
  margin: 0;
}

header {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem auto;
  border-radius: 10px;
  padding: 1rem;
  background-color: #58004d;
  color: white;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

#app ul {
  margin: 0;
  padding: 0;
  list-style: none;
}

#app li, #app form {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 1rem auto;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

#app h2 {
  font-size: 2rem;
  border-bottom: 4px solid #ccc;
  color: #58004d;
  margin: 0 0 1rem 0;
}

#app button {
  font: inherit;
  cursor: pointer;
  border: 1px solid #ff0077;
  background-color: #ff0077;
  color: white;
  padding: 0.05rem 1rem;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
}

#app button:hover,
#app button:active {
  background-color: #ec3169;
  border-color: #ec3169;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
}
</style>
