<template>
  <div class="product-container">
    <div class="image-wrapper">
      <img class="product-image" :src="productImage" />
    </div>
    <div class="product-info-wrapper">
      <p class="product-description">{{ productDescription }}</p>
      <div class="actual-price-wrapper">
        <div class="price-wrapper">
          <span class="price-symbol">₹</span
          ><span
            :class="{ active: discountedPrice != null }"
            class="price-info"
            >{{ priceWithCommas }}</span
          >
        </div>
        <div v-if="discountedPrice != null" class="price-wrapper">
          <span class="price-symbol">₹</span
          ><span class="price-info">{{ discountedPrice }}</span>
        </div>
      </div>
    </div>
    <div class="add-to-cart-wrapper">
      <input
        v-if="isProductAddedToCart"
        type="text"
        :value="quantityInCart"
        readonly
      />
      <button :class="{ active: isProductAddedToCart }" @click="addToCart">
        +
      </button>
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
    quantityInCart: Number,
    discountedPrice: Number,
    productId: Number,
  },
  data() {
    return {};
  },
  computed: {
    priceWithCommas() {
      return this.price
        .toString()
        .replace(/\B(?<!\.\d*)(?=(\d{3})+(?!\d))/g, ",");
    },
    isProductAddedToCart() {
      return this.quantityInCart > 0;
    },
  },
  methods: {
    addToCart() {
      this.$emit("add-to-cart", this.productId);
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
  text-overflow: ellipsis;
  overflow: hidden;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  margin-bottom: 10px;
}
.actual-price-wrapper {
  display: flex;
  column-gap: 5px;
}
.price-wrapper {
  color: #b12704;
  display: flex;
}
.price-wrapper .price-info.active {
  text-decoration: line-through;
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
.add-to-cart-wrapper {
  display: flex;
  align-items: center;

  height: 30px;

  position: absolute;
  right: 15px;
  bottom: 15px;
}
.add-to-cart-wrapper input {
  width: 30px;
  color: #f79b34;
  border: 2px solid #f79b34;
  border-right: none;

  outline: none;
  height: 100%;
  text-align: center;
  font-size: 15px;
  font-weight: 600;
  border-radius: 3px;
  border-top-right-radius: 0;
  border-bottom-right-radius: 0;
}
.add-to-cart-wrapper button {
  font-weight: bold;
  color: #fff;
  background-color: #f79b34;
  font-size: 18px;
  border: 2px solid #f79b34;
  border-left: none;
  border-radius: 3px;

  width: 42px;
  height: 100%;
}
.add-to-cart-wrapper button.active {
  border-top-left-radius: 0;
  border-bottom-left-radius: 0;
}
</style>