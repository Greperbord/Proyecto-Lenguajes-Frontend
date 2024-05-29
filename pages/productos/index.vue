<template>
  <v-app id="inspire">
    <v-app-bar app color="white">
      <v-container>
        <v-row>
          <a href="/inicio">
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
      <v-container>
        <h1 style="color: #0B254B; text-align: center;">
          Products
        </h1>
        <h2 class="small-heading" style="color: #5E6E89; text-align: center;">
          Order it for you or for your beloved ones
        </h2>
      </v-container>
      <v-container>
        <v-row v-for="(productRow, rowIndex) in productRows" :key="rowIndex">
          <v-col v-for="product in productRow" :key="product.id" cols="12" sm="6" md="3">
            <router-link :to="`/productos/${product.id}`">
              <v-card color="#F7F8FA" class="cursor-pointer">
                <v-img :src="require(`@/assets/images/${product.image}`)" />
                <v-card-subtitle>
                  <h1 class="small-heading" style="color: #1D293F; text-align: center;">
                    {{ product.name }}
                  </h1>
                </v-card-subtitle>
                <v-card-actions>
                  <v-spacer />
                  <span class="small-heading" style="color: #56B280;">
                    {{ product.price }}
                  </span>
                </v-card-actions>
              </v-card>
            </router-link>
          </v-col>
        </v-row>
      </v-container>
      <footer class="footer">
        <div class="footer-wrapper">
          <hr>
          <div class="footer-content">
            <div>
              <img :src="require('/assets/images/candleaf_white.svg')">
              <p style="color: white;">
                Your natural candle made for your home and for your wellness.
              </p>
            </div>
            <div class="footer-links">
              <div class="links-wrapper">
                <h3 style="color: #56B280">
                  Discovery
                </h3>
                <div class="links">
                  <a href="/new" style="color: white; text-decoration: none;">New season</a>
                  <a href="/searched" style="color: white; text-decoration: none;">Most searched</a>
                  <a href="/selled" style="color: white; text-decoration: none;">Most selled</a>
                </div>
              </div>
              <div class="links-wrapper">
                <h3 style="color: #56B280">
                  About
                </h3>
                <div class="links">
                  <a href="/help" style="color: white; text-decoration: none;">Help</a>
                  <a href="/ship" style="color: white; text-decoration: none;">Shipping</a>
                  <a href="/afillate" style="color: white; text-decoration: none;">Affiliate</a>
                </div>
              </div>
              <div class="links-wrapper">
                <h3 style="color: #56B280">
                  Info
                </h3>
                <div class="links">
                  <a href="/contact" style="color: white; text-decoration: none;">Contact us</a>
                  <a href="/privacy" style="color: white; text-decoration: none;">Privacy Policies</a>
                  <a href="/terms" style="color: white; text-decoration: none;">Terms &amp; Conditions</a>
                </div>
              </div>
            </div>
          </div>
        </div>
      </footer>
    </v-main>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      products: [
        { id: 1, name: 'Spiced Mint', price: '$9.99', image: 'p1.png' },
        { id: 2, name: 'Sweet Strawberry', price: '$9.99', image: 'p2.png' },
        { id: 3, name: 'Cool Blueberries', price: '$9.99', image: 'p3.png' },
        { id: 4, name: 'Juicy Lemon', price: '$9.99', image: 'p4.png' },
        { id: 5, name: 'Fresh Orange', price: '$9.99', image: 'p5.png' },
        { id: 6, name: 'Fragrant Cinnamon', price: '$9.99', image: 'p6.png' },
        { id: 7, name: 'Summer Cherries', price: '$9.99', image: 'p7.png' },
        { id: 8, name: 'Clean Lavender', price: '$9.99', image: 'p8.png' }
      ]
    }
  },
  computed: {
    productRows () {
      const rows = []
      for (let i = 0; i < this.products.length; i += 4) {
        rows.push(this.products.slice(i, i + 4))
      }
      return rows
    }
  }
}
</script>
