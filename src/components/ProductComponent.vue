<template>
  <div class="product-container">
    <div class="image-wrapper">
      <img class="product-image" :src="productImage" />
    </div>
    <div class="product-info-wrapper">
      <p class="product-description">{{ productDescription }}</p>
      <div class="price-wrapper">
        <span class="price-symbol">₹</span
        ><span class="price-info">{{ priceWithCommas }}</span>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    productImage: String,
    productDescription: String,
    rating: Number,
    price: Number,
  },
  computed: {
    priceWithCommas() {
      return this.price
        .toString()
        .replace(/\B(?<!\.\d*)(?=(\d{3})+(?!\d))/g, ",");
    },
  },
};
</script>
<style scoped>
.product-container {
  width: 300px;
  display: flex;
  flex-direction: column;
  margin: 10px;
  border: 1px solid #ddd;
  border-radius: 4px;
}
.image-wrapper {
  padding: 10px 0;
  display: flex;
  justify-content: center;
  background-color: #f8f8f8;
}
.product-image {
  height: 270px;
}
.product-info-wrapper {
  padding: 10px;
}
.product-description {
  font-weight: 600;
}
.price-wrapper {
  color: #b12704;
  display: flex;
}
.price-info {
  font-weight: 500;
  font-size: 20px;
}
.price-symbol {
  font-weight: 500;
  font-size: 14px;
  position: relative;
  top: 4px;
  margin-right: 2px;
}
</style>