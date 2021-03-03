<template>
  <div id="app" class="columns">
    <FilePicker :url.sync="url" v-bind:urls="urls"/>
    <SigPlot v-bind:url="url"/>
  </div>
</template>

<script>
import FilePicker from "./components/FilePicker";
import SigPlot from "./components/SigPlot";

export default {
  name: 'App',
  data() {
    return {
      url: '',
      urls: [],
    }
  },
  components: {
    FilePicker,
    SigPlot,
  },
  created() {
    // TODO
    // get the files on the server
    // fetch("sds/fs")
    //   .then(response => response.json())
    //   .then(data => this.urls = data)
    //   .catch(err => console.error(err))
    this.urls = [
        "foo",
        "bar",
        "baz",
    ]
  },
  methods: {
    setURL: url => this.url = url,
  },
}
</script>

<style>
html, body {
  height: 100%;
  width: 100%;
  margin: 0;
  padding: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  display: flex;
  min-height: 100vh;
  height: 100%;
}
</style>
