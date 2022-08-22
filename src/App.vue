<template>
  <section>
    <header><h1>My Friends</h1></header>
    <new-friend @add-contact="addContact"/>
    <ul v-for="friend in friends" :key="friend.id">
      <li>
        <friend-contact :friend="friend" @toggle-favorite="toggleFavorite" @delete-contact="deleteConatct"/>
      </li>
    </ul>
  </section>
</template>
<script>
export default {
  data: function () {
    return {
      friends: [
        {
          id: 'Bakr',
          name: 'BakrAl-Qassab',
          phone: '11223355888',
          email: 'bakr@baks.com',
          isFavorite: true
        },
        {
          id: 'Tomato',
          name: 'Tomato Tometo',
          phone: '11223355888',
          email: 'tomato@bakr.com',
          isFavorite: false,
        },
        {
          id: 'Potato',
          name: 'Potato Poteto',
          phone: '11223355888',
          email: 'potato@bakr.com',
          isFavorite: true,
        },

      ]
    }
  },
  methods: {
    toggleFavorite(Id) {
      const identifyFreinds = this.friends.find(friend => friend.id === Id);
      identifyFreinds.isFavorite = !identifyFreinds.isFavorite;
    },

    deleteConatct(Id) {
      this.friends = this.friends.filter(friend  => friend.id !== Id);
    },

    addContact(Name, phone, Email) {
      const newFriendConatct = {
        id: new Date().toISOString(),
        name: Name,
        phone: phone,
        email: Email,
        isFavorite: false
      };
      this.friends.push(newFriendConatct);

    }
  }
};

</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: 'Jost', sans-serif;
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

#app li,
#app form {
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
  margin-left: 10px;
}

#app button:hover,
#app button:active {
  background-color: #ec3169;
  border-color: #ec3169;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
}

#pp input {
  fonr: inherit;
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

</style>
