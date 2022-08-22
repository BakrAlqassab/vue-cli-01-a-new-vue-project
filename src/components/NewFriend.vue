<template>
  <form @submit.prevent="submitData">
    <div>
      <label>Name</label>
      <input v-model="enteredName" type="text">
    </div>
    <div>
      <label for="">Phone</label>
      <input v-model="enteredPhone" type="tel">
    </div>
    <div>
      <label for="">E-mail</label>
      <input type="email" v-model="enteredEmail">
    </div>

    <div>
      <button> Add Contact</button>
    </div>
  </form>
</template>

<script>
export default {
  emits: ['add-conatct'],
  data() {
    return {

      enteredName: '',
      enteredPhone: '',
      enteredEmail: ''
    }
  },
  methods: {
    submitData() {
      this.$emit('add-contact', this.enteredName, this.enteredPhone, this.enteredEmail);
      this.enteredName = '';
      this.enteredPhone = '';
      this.enteredEmail = '';
    }
  }
};
</script>
