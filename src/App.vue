<template>
  <div id="app">
    <div class="cell cell-map">
      <MapContainer
        :geojson="geojson"
        v-on:select="selected = $event"
      ></MapContainer>
    </div>
    <div class="cell cell-edit">
      <Edit :geojson="geojson" v-on:change="geojson = $event"> </Edit>
    </div>
    <div class="cell cell-inspect">
      <Inspect :feature="selected"></Inspect>
    </div>
  </div>
</template>

<script>
import MapContainer from "@/components/MapContainer";
import Edit from "@/components/Edit";
import Inspect from "@/components/Inspect";

export default {
  name: "App",
  components: {
    Inspect,
    Edit,
    MapContainer,
  },
  data: () => ({
    // this is the initial GeoJSON data
    selected: undefined,
    geojson: {
      type: "Feature",
      properties: {},
      geometry: {
        type: "Polygon",
        coordinates: [
          [
            [31.049999, -29.883333],
            [77.216721, 28.6448],
            [57.5724, -20.3104],
            // [-27.0703125, 43.58039085560784],
            // [-28.125, 23.563987128451217],
            // [-10.8984375, 32.84267363195431],
            // [-27.0703125, 43.58039085560784],
          ],
        ],
      },
    },
  }),
};
</script>

<style>
html,
body {
  height: 100%;
  margin: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  height: 100%;
  display: grid;
  grid-template-columns: 100vh;
  grid-auto-rows: 1fr;
  grid-gap: 1rem;
  padding: 1rem;
  box-sizing: border-box;
}
.cell {
  border-radius: 4px;
  background-color: lightgrey;
}
.cell-map {
  grid-column: 1;
  grid-row-start: 1;
  grid-row-end: 3;
}
.cell-edit {
  grid-column: 2;
  grid-row: 1;
}
.cell-inspect {
  grid-column: 2;
  grid-row: 2;
}
</style>
