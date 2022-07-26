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
      :productId="mobile.id"
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
      api: "http://localhost:3000/mobiles",
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
    addToCart(productId) {
      let index = this.mobileList.findIndex((mobileListElement) => {
        return mobileListElement.id == productId;
      });
      this.mobileList[index].quantityInCart += 1;
      console.log(this.mobileList[index]);
      const updated = this.mobileList[index];
      this.axios.put(this.api + "/" + updated.id, updated);
    },
    fetchMobileListFromDatabase() {
      this.axios.get(this.api).then((response) => {
        this.mobileList = response.data;
      });
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