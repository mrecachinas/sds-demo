<template>
  <div class="column is-one-fifth">
    <ul>
      <li
        v-for="(url, index) in urls"
        :key="index"
        :class="{ active: active === url }"
        v-on:click="setURL(url)">
        {{ url }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "FilePicker",
  data() {
    return {
      active: "",
    }
  },
  methods: {
    setURL(url) {
      this.active = url
      this.$emit('update:url', url)
    },
  },
  props: {
    selectHandler: Function,
    urls: Array,
  },
}
</script>

<style scoped>
.active {
  background-color: #d0d0d0;
}
.column {
  display: flex;
  min-height: 100vh;
  height: 100%;
  background-color: #f5f5f5;
  padding-right:0;
}
ul {
  color: #4a4a4a;
  font-weight: 600;
  width:100%;
  padding-top:20px;
}
li {
  padding-left:20px;
  cursor: pointer;
  list-style-type: none;
}
li:hover {
  background-color: #d0d0d0;
}
</style>