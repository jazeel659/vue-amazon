<template>
  <header>
    <img
      class="amazon-logo"
      src="https://pngimg.com/uploads/amazon/amazon_PNG11.png"
      alt="amazon-logo"
    />
    <input class="search-box" type="text" />
    <div class="mini-cart-wrapper">
      <img
        class="mini-cart-logo"
        src="@/assets/amazon-mini-cart-logo.svg"
        alt="mini-cart-logo"
      />
      <span class="cart-items">{{ numberOfItemsInCart }}</span>
    </div>
  </header>
</template>
<script>
export default {
  props: {
    numberOfItemsInCart: Number,
  },
  data() {
    return {};
  },
};
</script>
<style scoped>
header {
  background-color: #131921;
  display: flex;
  justify-content: space-between;
  align-items: center;
  position: fixed;
  top: 0;
  z-index: 1;
  width: 100%;

  padding: 10px;
}
.amazon-logo {
  width: 90px;
  position: relative;
  top: 8px;
}
.mini-cart-logo {
  width: 40px;
}
.search-box {
  flex: 1;
  margin: 0 15px;
  border-radius: 6px;
  height: 34px;
}
.cart-items {
  color: #f08804;
  font-weight: bold;
  font-size: 15px;
  width: 20px;
  text-align: center;
  position: absolute;
  right: 7px;
  top: -13px;
}
.mini-cart-wrapper {
  display: flex;
}
</style>
