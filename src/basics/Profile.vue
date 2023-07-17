<template>
  <div>
    <input type="text" v-model="city" @input="filterOptions" placeholder="Search...">
    <ul :class="['options-list', { 'show-list': city !== '' }]">
      <li v-for="option in filteredOptions" :key="option" @click="selectOption(option)">{{ option }}</li>
    </ul>
  </div>
</template>

<script>
import cities from './cities.json';
  export default {
    data() {
      return {
        city: '',
        options: cities,
        selectedOption: null
      };
    },
    computed: {
      filteredOptions() {
        if (!this.city) {
          return [];
        }

        const searchRegex = new RegExp(this.city, 'i');
        return this.options.filter(option => searchRegex.test(option) && option !== this.selectedOption);
      }
    },
    methods: {
      selectOption(option) {
        this.selectedOption = option;
        this.city = option;
        this.$nextTick(() => {
          const ulElement = document.querySelector('.options-list');
          ulElement.classList.remove('show-list');
        });
        console.log(this.selectedOption);
      }
    }
  };
</script>


<style>
.options-list {
  list-style-type: none;
  padding: 0;
  max-height: 200px; /* Set the maximum height for the list */
  overflow-y: auto; /* Enable vertical scrolling when the list exceeds the maximum height */
  position: absolute; /* Set the position to absolute */
  margin: 0;
  width: 200px !important;
  z-index: 999; /* Set a high z-index to make the list appear above other elements */
}

.options-list.show-list {
  display: block; /* Show the list when this class is applied */
  border: 1px solid #ccc; /* Add a border */
  border-radius: 4px; /* Add border radius for rounded corners */
}
li{
  display: block;
  cursor: pointer;
}
</style>