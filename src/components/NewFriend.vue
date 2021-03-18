<template>
    <form @submit.prevent="submitData">
        <div>
            <label for="name">Name</label>
            <input type="text" id="name" v-model="enteredName" >
        </div>
        <div>
            <label for="phone">Phone</label>
            <input type="tel" id="phone" v-model="enteredPhone">
        </div>
        <div>
            <label for="email">Email</label>
            <input type="email" id="email" v-model="enteredEmail">
        </div>
        <button type="submit">Submit</button>
    </form>
</template>

<script>
export default {
    emits: ['add-friend'],
    data() {
        return {
            enteredName: '',
            enteredPhone: '',
            enteredEmail: '',
        }
    },
    methods: {
        submitData(){
            this.$emit('add-friend', this.enteredName, this.enteredPhone, this.enteredEmail)
            this.enteredEmail = '';
            this.enteredPhone = '';
            this.enteredName = '';
        }
    }
}
</script>

<style scoped>
:root {
  --input-border: #8b8a8b;
  --input-focus-h: 245;
  --input-focus-s: 100%;
  --input-focus-l: 42%;
}
#app input {
  font: inherit;
  padding: 0.15rem;
}
#app label {
  font-weight: bold;
  margin-right: 1rem;
  width: 7rem;
  display: inline-block;
}
#app form div {
  margin: 1rem 0;
}
input + label {
  margin-top: 2rem;
}
input {
  font-size: 16px;
  font-size: max(16px, 1em);
  font-family: inherit;
  padding: 0.25em 0.5em;
  background-color: #fff;
  border: 2px solid var(8b8a8b);
  border-radius: 4px;
  transition: 180ms box-shadow ease-in-out;
  line-height: 1;
  height: 2.0rem;
}

button {
  color: #fff;
  border-radius: 8px;
  box-shadow: 0 3px 5px rgba(0, 0, 0, 0.18);
  padding: 6px 10px!important;
}
</style>