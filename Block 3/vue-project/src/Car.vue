<template>
  <div class="car">
    <h3>Name: {{ carName }}</h3>
    <p>Year: {{ carYear }}</p>
    <button @click="changeName">Change name</button>
    <button @click="changeFunc()">Change from parent</button>
    <button @click="updateCounter">Update counter</button>
  </div>
</template>

<script>
  import {eventEmitter} from "./main";

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
      },
      updateCounter() {
        //this.$emit('counterUpdated', this.counter + 1)
        eventEmitter.$emit('counterUpdated', 3)
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
