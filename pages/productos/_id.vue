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
            <v-icon>mdi-logout</v-icon>
          </a>
          <a style="position: absolute; right: 20px;" href="/cart">
            <v-img :src="require('@/assets/images/cart.svg')" />
          </a>
        </v-row>
      </v-container>
    </v-app-bar>
    <v-main class="grey lighten-2">
      <v-container>
        <v-row>
          <v-col cols="6">
            <v-card color="#F7F8FA">
              <v-img :src="require(`@/assets/images/${product.image}`)" />
              <v-card-text>
                <p style="text-align: center;">
                  All hand-made with natural soy wax, Candleaf is made for your pleasure moments.
                </p>
                <p style="color: #56B280; text-align: center;">
                  🚚 FREE SHIPPING
                </p>
              </v-card-text>
            </v-card>
          </v-col>
          <v-col cols="6">
            <v-card color="#F7F8FA" style="height: fit-content; width: 900px;">
              <v-card-title>
                <h1 style="color: #272727; text-align: center;">
                  {{ product.name }} Candleaf®
                </h1>
              </v-card-title>
              <p class="medium-heading" style="color: #56B280; text-align: center;">
                {{ product.price }}
              </p>
              <v-card-text>
                <v-row>
                  <v-col cols="6">
                    <div style="display: flex; flex-direction: column; align-items: left;">
                      <p class="small-heading" style="margin-bottom: 5px; color: #272727;">
                        Quantity
                      </p>
                      <div>
                        <v-btn class="quantity-container" elevation="2" style="color: #56B280;" @click="diminuirCantidad">
                          -
                        </v-btn>
                        <span class="quantity-value">{{ cantidad }}</span>
                        <v-btn class="quantity-container" elevation="2" style="color: #56B280;" @click="aumentarCantidad">
                          +
                        </v-btn>
                      </div>
                    </div>
                  </v-col>
                  <v-col cols="6">
                    <div style="display: flex; flex-direction: column; align-items: flex-start;">
                      <v-card color="#F7F8FA" style="height: 350px;">
                        <v-radio-group v-model="selectedOption">
                          <v-radio label="One time purchase" value="one_time" />
                          <v-radio label="Subscribe and delivery every" value="subscribe" />
                        </v-radio-group>
                        <v-expansion-panels v-if="selectedOption === 'subscribe'" style="color: #E7E7E7;">
                          <v-expansion-panel>
                            <v-expansion-panel-header>
                              4 weeks
                            </v-expansion-panel-header>
                            <v-expansion-panel-content>
                              Lorem ipsum dolor, sit amet consectetur adipisicing elit. Ab, at?
                            </v-expansion-panel-content>
                          </v-expansion-panel>
                        </v-expansion-panels>
                        <h1 class="small-heading">
                          Subscribe now and get the 10% of discount on every recurring order. The discount will be applied at checkout.
                          <p class="small-heading">
                            <router-link to="/productos" style="color: #56B280;">
                              See details
                            </router-link>
                          </p>
                        </h1>
                        <v-row justify="center">
                          <v-btn elevation="2" large color="#56B280" @click="agregarCarrito">
                            <v-icon color="#FFFFFF">
                              mdi-cart
                            </v-icon>
                            <span style="color: #FFFFFF; margin-left: 8px;">
                              + Add to cart
                            </span>
                          </v-btn>
                        </v-row>
                      </v-card>
                    </div>
                  </v-col>
                </v-row>
              </v-card-text>
              <v-row justify="center" color="#F7F8FA">
                <v-card style="width: 400px;" elevation="0" color="#F7F8FA">
                  <h1 class="small-s-heading" style="text-align: center;">
                    Wax: Top grade Soy wax that delivers a smoke less, consistent burn
                  </h1>
                  <h1 class="small-s-heading" style="text-align: center;">
                    Fragrance: Premium quality ingredients with natural essential oils
                    <h2 class="small-s-heading">
                      Burning Time: 70-75 hours
                    </h2>
                    <h2 class="small-s-heading">
                      Dimension: 10cm x 5cm
                    </h2>
                    <h2 class="small-s-heading">
                      Weight: 400g
                    </h2>
                  </h1>
                </v-card>
              </v-row>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
      <div style="margin-top: 50px;" />
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
      product: {},
      cantidad: 1,
      selectedOption: 'one_time',
      products: [
        { id: 1, name: 'Spiced Mint', price: '$9.99', image: 'p1.png', description: 'A refreshing blend of mint and spices.' },
        { id: 2, name: 'Sweet Strawberry', price: '$9.99', image: 'p2.png', description: 'A delightful product.' },
        { id: 3, name: 'Cool Blueberries', price: '$9.99', image: 'p3.png', description: 'An amazing product.' },
        { id: 4, name: 'Juicy Lemon', price: '$9.99', image: 'p4.png', description: 'A fantastic product.' },
        { id: 5, name: 'Fresh Orange', price: '$9.99', image: 'p5.png', description: 'A wonderful product.' },
        { id: 6, name: 'Fragrant Cinnamon', price: '$9.99', image: 'p6.png', description: 'A great product.' },
        { id: 7, name: 'Summer Cherries', price: '$9.99', image: 'p7.png', description: 'A superb product.' },
        { id: 8, name: 'Clean Lavender', price: '$9.99', image: 'p8.png', description: 'A fantastic product.' }
      ]
    }
  },
  created () {
    this.loadProduct()
  },
  methods: {
    loadProduct () {
      const productId = parseInt(this.$route.params.id, 10)
      const product = this.products.find(product => product.id === productId)
      if (product) {
        this.product = product
      } else {
        this.$nuxt.error({ statusCode: 404, message: 'Product not found' })
      }
    },
    aumentarCantidad () {
      this.cantidad++
    },
    diminuirCantidad () {
      if (this.cantidad > 1) {
        this.cantidad--
      }
    },
    agregarCarrito () {
      const newItem = {
        productId: this.product.id,
        name: this.product.name,
        image: this.product.image,
        cantidad: this.cantidad,
        price: this.product.price
      }
      const cart = JSON.parse(localStorage.getItem('cart')) || []
      const existingItemIndex = cart.findIndex(item => item.productId === newItem.productId)

      if (existingItemIndex !== -1) {
        cart[existingItemIndex].cantidad += newItem.cantidad
      } else {
        cart.push(newItem)
      }

      localStorage.setItem('cart', JSON.stringify(cart))
      this.$router.push({ name: 'cart' })
    }
  }
}
</script>
