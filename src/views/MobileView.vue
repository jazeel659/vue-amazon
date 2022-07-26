<template>
  <NavBarComponent :numberOfItemsInCart="totalQtyInCart" />
  <div class="product-list-wrapper">
    <ProductComponent
      v-for="mobile in mobileList"
      :key="mobile.productDescription"
      :productImage="mobile.productImage"
      :productDescription="mobile.productDescription"
      :rating="mobile.rating"
      :price="mobile.price"
      :quantityInCart="mobile.quantityInCart"
      :discountedPrice="mobile.discountedPrice"
      @add-to-cart="addToCart"
    />
  </div>
</template>
<script>
import ProductComponent from "../components/ProductComponent.vue";
import NavBarComponent from "../components/NavBarComponent.vue";

export default {
  components: { ProductComponent, NavBarComponent },
  created() {
    this.fetchMobileListFromDatabase();
  },
  data() {
    return {
      mobileList: [],
    };
  },

  computed: {
    totalQtyInCart() {
      let sum = 0;
      for (let mobileListElement of this.mobileList) {
        sum += mobileListElement.quantityInCart;
      }

      return sum;
    },
    totalChar() {
      return this.myName.length;
    },
  },
  methods: {
    addToCart(productDescription) {
      let index = this.mobileList.findIndex((mobileListElement) => {
        return mobileListElement.productDescription == productDescription;
      });
      this.mobileList[index].quantityInCart += 1;
      console.log(index);
    },
    fetchMobileListFromDatabase() {
      this.mobileList = [
        {
          productImage:
            "https://m.media-amazon.com/images/I/71AvQd3VzqL._AC_UL480_FMwebp_QL65_.jpg",
          productDescription:
            "OnePlus Nord CE 2 Lite 5G (Blue Tide, 6GB RAM, 128GB Storage)",
          rating: 4,
          price: 19999,
          discountedPrice: 15000,
          quantityInCart: 0,
        },
        {
          productImage:
            "https://m.media-amazon.com/images/I/911TJ1CDbLL._AC_UL480_FMwebp_QL65_.jpg",
          productDescription:
            "Redmi 9 Activ (Carbon Black, 4GB RAM, 64GB Storage)",
          rating: 4,
          price: 22000,
          discountedPrice: null,

          quantityInCart: 0,
        },
        {
          productImage:
            "https://m.media-amazon.com/images/I/71k86pEH5LS._AC_UL480_FMwebp_QL65_.jpg",
          productDescription:
            "Oppo A54 (Starry Blue, 6GB RAM, 128GB Storage) with No Cost EMI & Additional Exchange Offers",
          rating: 4,
          price: 9999,
          discountedPrice: 7000,

          quantityInCart: 0,
        },
        {
          productImage:
            "https://m.media-amazon.com/images/I/81QqVNKWtML._AC_UL480_FMwebp_QL65_.jpg",
          productDescription:
            "realme narzo 50i (Mint Green, 2GB RAM+32GB Storage) - 6.5 inch Large Display | 5000mAh Battery)",
          rating: 4,
          price: 49999,
          discountedPrice: null,

          quantityInCart: 0,
        },
      ];
    },
  },
};
</script>

<style scoped>
.product-list-wrapper {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  padding: 20px;
  margin-top: 45px;
}
</style>