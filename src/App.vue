<template>
  <div id="app">
    <Catalog
        v-for="(product, id) of ProductList.catalog"
        v-bind:product="product"
        v-bind:key="id"
    />
    <button
        class="button__state"
        v-on:click="isShowJson = !isShowJson"
    >{{ isShowJson ? "Скрыть" : "Показать" }} состояние JSON
    </button>
    <button
        v-on:click="resetStateJson()"
    >
      Сбросить состояние JSON
    </button>
    <pre v-if="isShowJson">
      {{ ProductList }}
    </pre>
  </div>
</template>

<script>
import Catalog from "./components/Catalog";
import ProductList from "./ProductList";

export default {
  name: 'App',
  components: {
    Catalog,
  },

  methods: {
    resetStateJson() {
      Object.assign(this.$data.ProductList, ProductList())
    },
  },

  data() {
    return {
      ProductList: ProductList(),
      isShowJson: false,

    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

button {
  margin: 5px;
  padding: 10px;
  border-radius: 10px;
  border: #2c3e50 solid 2px;
  color: #2c3e50;
  font-weight: bold;
  font-size: 14px;
  transition: 0.3s;
}

button:hover {
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
}

.button__state {
  min-width: 210px;
  border-radius: 10px;
}
</style>
