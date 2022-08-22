<template>
  <li>
    <h2>{{ friend.name }}{{ friend.isFavorite ? '  (Favorite)' : '' }}</h2>
    <button @click="toggleFavorite">Favorite</button>
    <button @click="toggleDetails">{{ detailsAreVisible ? 'Hide' : 'Show' }} Details</button>
    <ul v-if="detailsAreVisible">
      <li><strong>Phone: </strong> {{ friend.phone }}</li>
      <li><strong>Email: </strong> {{ friend.email }}</li>
    </ul>
    <button @click="deleteContact">Delete</button>
  </li>
</template>

<script>
export default {
  data() {
    return {
      detailsAreVisible: false,
    }
  },
  emits: ['toggle-favorite','delete-contact'],
  // emits: {
  //   'toggle-favorite': function (id) {
  //     if (id) {
  //       return true
  //     } else {
  //       console.warn('ID is missing')
  //       return false
  //     }
  //
  //   }
  // },
  props: {
    friend: {
      type: Object,
      required: true,
    },
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFavorite() {
      this.$emit('toggle-favorite', this.friend.id)
    },
    deleteContact() {
      this.$emit('delete-contact',this.friend.id)

    }
  }

};
</script>
