<template>
    <div class="travels">
        <ul>
        <li v-for="travel in travels" :key="travel.id">
          <Travel v-bind:travel="travel" />
          <a class="deleteBtn" @click.prevent="remove(travel)">Delete</a>
        </li>
      </ul>
      <form class="add-travel" @keydown.enter.prevent="add" >
          <input type="input" v-model="newTravel" /> Press ENTER to save
      </form>
      <div>Calculated price: {{ totalPrice }} EUR</div>
    </div>

</template>

<script>
import Travel from "./Travel.vue"

export default {
  name: 'Travels',
  components: {
    Travel
  },
  data () {
      return {
        travels: [],
        newTravel: "",
        totalPrice: 0,
        nextIdOfItem: 1
      }
  },
  methods: {
      add() {
        if (this.newTravel !== "") {
            this.travels.push({ name: this.newTravel, price: Math.ceil(Math.random()*100), id: this.nextIdOfItem });
            this.nextIdOfItem++;
            this.newTravel = "";
            this.calculateTotalPrice();
        }
      },

      remove(travel) {
          this.travels = this.travels.filter(item => item !== travel);
          this.calculateTotalPrice();
      },

      calculateTotalPrice() {
          if (this.travels.length === 0) {
            this.totalPrice = 0;
          } else {
            this.totalPrice = this.travels.map(travel => travel.price).reduce((prev, next) => prev + next);
          }

      }
  }
}
</script>

<style scoped>
    ul {
        list-style-type: none;
    }

    ul > li {
        margin-bottom: 10px;
    }

    a.deleteBtn {
        border: red 1px solid;
        margin-left: 10px;
        cursor: pointer;
        border-radius: 6px;
        color: red;
        padding: 3px;
    }
</style>
