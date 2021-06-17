<template>
  <ul>
    <li>
      <input
          type="checkbox"
          v-model="product.selected"
      >
      <button
          class="button__hide"
          v-if="product.catalog"
          v-on:click="isShowProduct = !isShowProduct"
      >{{ isShowProduct ? "-" : "+" }}
      </button>
      {{ product.name }}
      <Catalog
          v-for="(product, id) of product.catalog"
          v-bind:product="product"
          v-bind:key="id"
          v-show="isShowProduct"
          v-bind:selfSelected="product.selected"
      />
    </li>
  </ul>
</template>

<script>
export default {
  name: "Catalog",

  props: {
    product: Object,
    selfSelected: {
      type: Boolean,
      default: false,
    },
  },

  watch: {
    selfSelected(valueSelectProduct) {
      this.product.selected = valueSelectProduct;
      this.selected = valueSelectProduct;
      this.$emit("update:selected", valueSelectProduct)
    },
  },

  data() {
    return {
      isShowProduct: false,
    }
  },
}
</script>

<style scoped>
li {
  vertical-align: middle;
}

.button__hide {
  min-width: 30px;
  max-height: 30px;
  padding: 5px;
  border-radius: 50%;
}

input:hover {
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.3);
}

</style>