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
  data() {
    return {
      numberOfItemsInCart: 0,
    };
  },
};
</script>
<style scoped>
header {
  background-color: #131921;
  display: flex;
  justify-content: space-between;
  align-items: center;
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
  font-size: 18px;
  position: relative;
  right: 20px;
  top: -9px;
}
.mini-cart-wrapper {
  display: flex;
}
</style>
