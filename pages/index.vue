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
          <router-link to="/productos" style="text-decoration: none;">
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
        <div>
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
        </div>
      </div>

      <div style="background-color: #F7F8FA; align-items: center; display: flex; justify-content: space-between; margin: 0 auto; flex-wrap: wrap-reverse;">
        <div style="margin-bottom: 20px;  margin-left: 150px;">
          <h1>Clean and fragrant soy wax</h1>
          <p style="color: #56B280;">
            Made for your home and for your wellness
          </p>
          <div>
            <p>
              <v-icon>mdi-check-circle-outline</v-icon>
              Eco-sustainable:All recyclable materials, 0% CO2 emissions.
            </p>
            <p>
              <v-icon>mdi-check-circle-outline</v-icon>
              Hyphoallergenic: 100% natural, human friendly ingredients.
            </p>
            <p>
              <v-icon>mdi-check-circle-outline</v-icon>
              Handmade: All candles are craftly made with love.
            </p>
            <p>
              <v-icon>mdi-check-circle-outline</v-icon>
              Long burning: No more waste. Created for last long.
            </p>
          </div>
          <button class="learn-more">
            Learn more
          </button>
        </div>
        <div style="overflow-clip-margin: content-box; overflow: clip; margin-right: 150px;">
          <v-img :src="require('@/assets/images/promotion-img.svg')" />
        </div>
      </div>

      <div class="testimonial">
        <h1>Testimonials</h1>
        <p>Some quotes from our happy customers</p>
        <div class="testimonials">
          <div class="testimonial-card">
            <div style="text-align: center;">
              <div class="avatar">
                <v-img :src="require('@/assets/images/Luisa.svg')" />
              </div>
              <div>
                <span>
                  <v-img :src="require('@/assets/images/star1.svg')" />
                </span>
              </div>
              <p>"“I love it! No more air fresheners”"</p>
              <span style="color: #7c8087; font-size: 18px;">Luisa</span>
            </div>
          </div>
          <div class="testimonial-card">
            <div style="text-align: center;">
              <div class="avatar">
                <v-img :src="require('@/assets/images/Edoardo.svg')" />
              </div>
              <div>
                <span>
                  <v-img :src="require('@/assets/images/star2.svg')" />
                </span>
              </div>
              <p>"Reccomended for everyone"</p>
              <span style="color: #7c8087; font-size: 18px;">Edoardo</span>
            </div>
          </div>
          <div class="testimonial-card">
            <div style="text-align: center;">
              <div class="avatar">
                <v-img :src="require('@/assets/images/Mart.svg')" />
              </div>
              <div>
                <span class="star">
                  <v-img :src="require('@/assets/images/star2.svg')" />
                </span>
              </div>
              <p>"“Looks very natural, the smell is awesome!“"</p>
              <span style="color: #7c8087; font-size: 18px;">Mart</span>
            </div>
          </div>
        </div>
      </div>

      <div class="popular-product">
        <h3>Popular</h3>
        <p>Our top selling product that you may like</p>
        <div>
          <v-row v-for="(productRow, rowIndex) in topProducts" :key="rowIndex">
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
        </div>
      </div>

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
  name: 'IndexPage',
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
    },
    topProducts () {
      const rows = []
      for (let i = 0; i < this.products.length; i += 8) {
        rows.push(this.products.slice(i, i + 4))
      }
      return rows
    }
  },
  auth: false
}
</script>
