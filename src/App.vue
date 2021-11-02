<template>
    <div id="app">
        <div class="office">
            <Map
                @showInfo="showInfo"
                @hideInfo="hideInfo"
                v-click-outside="hideInfo"/>
            <SideMenu
                :person="selectedEmployee"
                :isUserOpened="isUserOpened"
                @update:isUserOpened="hideInfo"/>
        </div>
    </div>
</template>

<script>
import Map from "./components/Map.vue";
import SideMenu from "./components/SideMenu.vue";
import people from '@/assets/data/people.json';
import ClickOutside from 'vue-click-outside';

export default {
  name: "App",
  components: {
    Map,
    SideMenu,
  },
  data() {
      return {
          selectedEmployee: null,
          isUserOpened: false,
      };
  },
  methods: {
    showInfo(id) {
      this.selectedEmployee = people.find((elem) => elem.tableId === id);
      this.isUserOpened = true;
    },
    hideInfo() {
        this.isUserOpened = false;
        this.selectedEmployee = null;
    },
  },
  directives: {
    ClickOutside
  },
};
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    color: #2c3e50;
    background-color: #fafafa;
    padding: 24px;
    box-sizing: border-box;
}

html,
body,
#app {
    height: 100%;
}

* {
    box-sizing: border-box;
}

h3 {
    margin-top: 0px;
}

.office {
    display: grid;
    grid-template-columns: 1fr 320px;
    border-radius: 6px;
    border: 1px solid #ccd8e4;
    height: 100%;
    background: white;
    max-width: 1500px;
    margin: 0 auto;
}
</style>
