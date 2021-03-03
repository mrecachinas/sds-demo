<template>
  <div class="column">
    <div class="plot"></div>
  </div>
</template>

<script>
import { Plot } from "sigplot"
export default {
  name: "SigPlot",
  data() {
    return {
      plot: null,
      layer: null,
    }
  },
  mounted() {
    this.plot = new Plot(this.$el, {})
  },
  props: {
    url: String,
  },
  watch: {
    url(newURL, oldURL) {
      if (!oldURL) {
        this.layer = this.plot.overlay_href(newURL, null, {layerType: "SDS"})
      } else if (newURL !== oldURL) {
        this.plot.remove_layer(this.layer)
        this.plot.overlay_href(newURL, null, {layerType: "SDS"})
      }
    }
  },
}
</script>

<style scoped>
.column {
  display: flex;
  min-height: 100vh;
  height: 100%;
  padding-left:0;
}
.plot {
  height:100%;
  min-height: 100vh;
  display: flex;
}
</style>