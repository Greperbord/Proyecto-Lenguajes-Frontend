<template>
  <v-app id="inspire">
    <v-app-bar app color="white">
      <v-container>
        <v-row>
          <a href="/">
            <v-img :src="require('@/assets/images/logo.svg')" />
          </a>
        </v-row>
      </v-container>
      <v-container>
        <v-row justify="space-between">
          <router-link to="/productos">
            <a style="color: black">Discovery</a>
          </router-link>
          <a style="color: black">About</a>
          <a style="color: black">Contact us</a>
        </v-row>
      </v-container>
      <v-container>
        <v-row>
          <a style="position: absolute; right: 70px;" href="/">
            <v-img :src="require('@/assets/images/account.svg')" />
          </a>
          <a style="position: absolute; right: 20px;" href="/cart">
            <v-img :src="require('@/assets/images/cart.svg')" />
          </a>
        </v-row>
      </v-container>
    </v-app-bar>

    <v-main class="grey lighten-2">
      <div style="background-color: aqua;">
        <v-img :src="require('@/assets/images/fondo.svg')">
          <v-card color="#F7F8FACC" style="width: 500px; height: 220px; margin-top: 220px; margin-left: 350px; border-radius: 2px;" align="center">
            <v-title>
              <h1>🌱</h1>
            </v-title>
            <v-card-subtitle>
              <h1 style="color: black">
                The nature candle
              </h1>
            </v-card-subtitle>
            <v-card-text style="color: black">
              All handmade with natural soy wax, Candleaf is a companion for all your pleasure moments.
            </v-card-text>
            <v-card-actions style="margin-left: 90px;">
              <router-link to="/productos">
                <v-img :src="require('@/assets/images/botonxd.svg')" />
              </router-link>
            </v-card-actions>
          </v-card>
        </v-img>
      </div>

      <div style="text-align: center; background-color: white;">
        <h2 style="color: #0B254B;">
          Products
        </h2>
        <p style="color: #5E6E89;">
          Order it for you or for your beloved ones
        </p>
        <div class="products">
          <a href="/item1" style="text-decoration: none; text-transform: none;">
            <div class="product-card">
              <div class="product-background">
                <img :src="require('/assets/images/product1.svg')">
              </div>
              <div class="product-card-footer">
                <h4>Spiced Mint</h4>
                <p>$12.56</p>
              </div>
            </div>
          </a>
          <a href="/item2">
            <div class="product-card">
              <div class="product-background">
                <img :src="require('/assets/images/product2.svg')">
              </div>
              <div class="product-card-footer">
                <h4>Sweet Strawberry</h4>
                <p>$9.99</p>
              </div>
            </div>
          </a>
          <a href="/item3">
            <div class="product-card">
              <div class="product-background">
                <img :src="require('/assets/images/product3.svg')">
              </div>
              <div class="product-card-footer">
                <h4>Cool Blueberris</h4>
                <p>$9.99</p>
              </div>
            </div>
          </a>
          <a href="/item4">
            <div class="product-card">
              <div class="product-background">
                <img :src="require('/assets/images/product4.svg')">
              </div>
              <div class="product-card-footer">
                <h4>Juicy Lemon</h4>
                <p>$9.99</p>
              </div>
            </div>
          </a>
          <a href="/item5">
            <div class="product-card">
              <div class="product-background">
                <img :src="require('/assets/images/product5.svg')">
              </div>
              <div class="product-card-footer">
                <h4>Stary Golden</h4>
                <p>$9.99</p>
              </div>
            </div>
          </a>
          <a href="/item6">
            <div class="product-card">
              <div class="product-background">
                <img :src="require('/assets/images/product6.svg')">
              </div>
              <div class="product-card-footer">
                <h4>Fragrant Cinnamon</h4>
                <p>$9.99</p>
              </div>
            </div>
          </a>
          <a href="/item7">
            <div class="product-card">
              <div class="product-background">
                <img :src="require('/assets/images/product7.svg')">
              </div>
              <div class="product-card-footer">
                <h4>Summer Cherrys</h4>
                <p>$9.99</p>
              </div>
            </div>
          </a>
          <a href="/item8">
            <div class="product-card">
              <div class="product-background">
                <img :src="require('/assets/images/product8.svg')">
              </div>
              <div class="product-card-footer">
                <h4>Clean Lavander</h4>
                <p>$9.99</p>
              </div>
            </div>
          </a>
        </div>
      </div>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: 'IndexPage',
  auth: false
}
</script>

<style scoped>
.products {
  margin-left: 130px;
  grid-gap: 18px;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  width: 80%;
}

.product-card {
  border-radius: 5px;
    cursor: pointer;
    display: flex;
    flex-direction: column;
    height: 230px;
    transition: all .3s ease-in-out;
}

.product-background {
    background-color: #f7f8fa;
    border-top-left-radius: 5px;
    border-top-right-radius: 5px;
    height: 152px;
    margin-bottom: 0;
    width: 100%;
}

.product-card-footer {
    background-color: #fff;
    border-bottom-left-radius: 5px;
    border-bottom-right-radius: 5px;
    height: 76px;
}
</style>
