<template>
  <div class="car">
    <h3>Name: {{ carName }}</h3>
    <p>Year: {{ carYear }}</p>
    <button @click="changeName">Change name</button>
    <button @click="changeFunc()">Change from parent</button>
  </div>
</template>

<script>
  export default {
    props: {
      carName: {
        type: String,
        required: true,
        default: 'Default name'
      },
      carYear: Number,
      changeFunc: Function
    },
    methods: {
      changeName() {
        this.carName = 'Mazda';
        this.$emit('nameChanged', this.carName)
      }
    }
  }
</script>

<style>
  .car{
    border: 1px solid black;
  }
  .car h3 {
    margin-bottom: 5px;
  }
</style>
