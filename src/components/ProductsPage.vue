<template>
  <v-container>
    <v-dialog v-model="helpDialog">
      <v-card>
        <v-card-text>
          <h2>GBox Hobby</h2>
          <p>
            Shop chuyên cung cấp các sản phẩm mô hình lắp ráp từ Nhật Bản và
            Trung Quốc như Gunpla, Gundam, 30MM, LBX,... với giá cả hợp lý.
          </p>
          <ul>
            <li>
              Facebook Page:
              <a href="https://fb.com/gboxstorevn" target="_blank"
                >GBox Hobby</a
              >
              (hãy follow để cập nhật thông tin hàng hóa và các chương trình
              khuyến mãi nhé)
            </li>
            <li>Hotline: <a href="tel: 0981658640">098 165 8640</a></li>
            <li>
              Địa chỉ:
              <a href="https://goo.gl/maps/ZbsPL4uhcaEesYy27" target="_blank"
                >Dương Văn An, Mân Thái, Sơn Trà, Đà Nẵng</a
              >
            </li>
          </ul>
          <h2>Kênh bán hàng</h2>
          <ul>
            <li>
              Mua hàng trực tiếp tại Đà Nẵng: Giá sản phẩm trên website này là
              giá cao nhất mà bạn phải trả (chiết khấu khác dựa trên độ đốt tiền
              và tình cảm của shop với bạn :3)
            </li>
            <li>
              Mua hàng online: liên hệ đặt hàng qua Facebook Page:
              <a href="https://fb.com/gboxstorevn" target="_blank">GBox Hobby</a
              >; Có 2 hình thức: bank full và COD. Phí ship sẽ được báo lại cho
              bạn trước khi quyết định đặt hàng.
            </li>
            <li>
              Mua hàng qua Shopee:
              <a href="https://shp.ee/2dfifmb" target="_blank">Shopee</a>; Nếu
              thấy phí ship cao hoặc mua nhiều sản phẩm với giá cao, hãy chat
              với Shop để nhận được offer tốt hơn.
            </li>
          </ul>
        </v-card-text>
        <v-card-subtitle
          >From GBox with <v-icon icon="mdi-heart"></v-icon
        ></v-card-subtitle>
        <v-card-actions>
          <v-btn color="primary" block @click="helpDialog = false">Close</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
    <v-row dense no-gutters class="search-header">
      <v-col cols="8">
        <v-text-field
          color="#fff"
          v-model="searchText"
          label="Search"
          placeholder="HGUC, HG, Zaku,..."
          clearable
          @update:modelValue="searchProducts"
          hide-details="true"
          class="pb-4 pt-4"
        ></v-text-field>
      </v-col>
      <v-col cols="2" align-self="center" align="center">
        <v-btn
          icon="mdi-facebook-messenger"
          color="rgb(0, 153, 255)"
          class="ma-2"
          variant="outlined"
          href="https://m.me/gboxstorevn"
          target="_blank"
        ></v-btn>
      </v-col>
      <v-col
        cols="2"
        align-self="center"
        align="center"
        @click="helpDialog = true"
      >
        <v-btn icon="mdi-help-box" color="red" class="ma-2" variant="outlined">
        </v-btn>
      </v-col>
    </v-row>
    <v-row dense>
      <ProductItem
        v-for="product in filteredProducts"
        :key="product.id"
        :id="product.id"
        :name="product.name"
        :price="product.price"
        :shopeePrice="product.shopeePrice"
        :shopeeLink="product.shopeeLink"
        :image="product.image"
      ></ProductItem>
    </v-row>
  </v-container>
</template>

<script>
import ProductItem from './ProductItem.vue'
import products from '../products.json'
export default {
  data() {
    return {
      products: [],
      filteredProducts: [],
      searchText: null,
      helpDialog: false,
    }
  },
  mounted() {
    this.products = products
    this.filteredProducts = [...this.products]
  },
  computed: {},
  methods: {
    searchProducts() {
      const searchKeys = this.searchText
        .toLowerCase()
        .split(' ')
        .filter((key) => key)

      if (searchKeys.length === 0) {
        this.filteredProducts = [...this.products]
        return
      }

      this.filteredProducts = this.products.filter((product) => {
        const name = product.name.toLowerCase()
        return searchKeys.some((key) => {
          return name.includes(key)
        })
      })
    },
  },
  components: {
    ProductItem,
  },
}
</script>

<style scoped>
.search-header {
  position: sticky;
  top: -0.2px;
  z-index: 999;
  background: rgb(var(--v-theme-background));
}
</style>
