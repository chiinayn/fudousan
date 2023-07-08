<template>
  <transition name="fade">
    <ModalComponent @setModalStatFalse="modalStat = $event" :rooms="rooms" :clickNum="clickNum" :modalStat="modalStat" />
  </transition>
  <div class="menu">
    <a v-for="(v) in memus" :key="v ">{{ v }}</a>
  </div> 
  <DiscountBanner v-if="showDiscount == true"/>
  <button @click="priceSort()" class="buttonMargin">値段でソート</button>
  <button @click="sortBack()" class="buttonMargin">戻す</button>
  <CardComponent @openModal="modalStat = true; clickNum = $event" v-for="(room,i) in rooms" :key="room" :room="room" :index="i" :reports="reports" />
</template>

<script>
  import room_data from './data.js';
  import DiscountBanner from './DiscountBanner.vue';
  import ModalComponent from './ModalComponent.vue';
  import CardComponent from './CardComponent.vue';

export default {
    name: 'App',
    data() {
      return {
        showDiscount : true,
        roomsOrigin : [...room_data],
        clickNum : 0,
        rooms : room_data,
        modalStat : false,
        reports : [0,0,0],
        memus : ['Home', 'Shop','About'],
      }
    },
    methods : {
      priceSort() {
        this.rooms.sort(function(a,b){
          return a.price - b.price;
        });
      },
      sortBack() {
        this.rooms = [...this.roomsOrigin];
      }

    },
    mounted() {
      setTimeout(() => {
        this.showDiscount = false;
      }, 2000);
    },
    components: {
      DiscountBanner,
      ModalComponent,
      CardComponent,
    },
}
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
  }
  body {
    margin: 0;
  }
  div {
    box-sizing: border-box;
  }
  .buttonMargin {
    margin: 5px;
  }

  .menu {
  background-color: darkslateblue;
    padding: 10px;
    border-radius: 5px;
  }
  .menu a {
    color: white;
    padding: 10px;
  }
  .discount {
    background: #eee;
    padding: 10px;
    margin: 10px;
    border-radius: 5px;
  }
</style>
