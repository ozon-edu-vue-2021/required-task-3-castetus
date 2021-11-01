<template>
  <div class="map">
    <h3>Карта офиса</h3>

    <div v-if="!isLoading" class="map-root">
      <MapImg ref="svg" />
    </div>
    <div v-else>Loading...</div>
  </div>
</template>

<script>
import MapImg from "@/assets/images/map.svg";
import * as d3 from "d3";

export default {
  components: {
    MapImg,
  },
  data() {
    return {
      isLoading: false,
      svg: null,
      g: null,
    };
  },
  mounted() {
    this.svg = d3.select(this.$refs.svg);
    this.g = this.svg.select("g");
    if (this.g) {
      this.drawTables();
    } else {
      console.log("error");
    }
  },
  methods: {
    drawTables() {
      const tablesGroup = this.g.append("g").classed("groupPlaces", true);
    },
  },
};
</script>

<style scoped>
.map {
  height: 100%;
  width: 100%;
  padding: 24px;
  overflow: hidden;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
}

.map-root {
  height: 100%;
  width: 100%;
  overflow: hidden;
  box-sizing: border-box;
}

h3 {
  margin-top: 0px;
}

::v-deep svg {
  height: 100%;
  width: 100%;
}

::v-deep .table {
  cursor: pointer;
}
</style>
