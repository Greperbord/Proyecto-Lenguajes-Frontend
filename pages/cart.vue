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
      <v-container class="cart-container">
        <v-row>
          <v-col cols="12">
            <v-card class="cart-card">
              <h1 class="medium-m-heading" style="text-align: center;">
                Your cart items
              </h1>
              <router-link to="/productos">
                <p style="color: #56B280; text-align: center;">
                  Back to shopping
                </p>
              </router-link>
              <v-card-text>
                <div>
                  <v-row>
                    <v-col cols="3">
                      <p style="color: #272727;" class="medium-heading">
                        Product
                      </p>
                    </v-col>
                    <v-col cols="3" class="medium-heading">
                      <p style="color: #272727;">
                        Price
                      </p>
                    </v-col>
                    <v-col cols="3" class="medium-heading">
                      <p style="color: #272727">
                        Quantity
                      </p>
                    </v-col>
                    <v-col cols="3">
                      <p style="color: #272727;" class="medium-heading">
                        Total:
                      </p>
                    </v-col>
                  </v-row>
                  <v-divider inset />
                  <div v-for="item in cart" :key="item.productId">
                    <v-row>
                      <v-col cols="3">
                        <p style="color: #272727;" class="medium-heading">
                          {{ item.name }} Candleaf®
                        </p>
                        <v-btn text style="color: #56B280;" @click="removeItem(item.productId)">
                          Remove
                        </v-btn>
                        <v-img :src="require(`@/assets/images/${item.image}`)" />
                      </v-col>
                      <v-col cols="3">
                        <p style="color: #272727;" class="small-heading ">
                          {{ item.price }}
                        </p>
                      </v-col>
                      <v-col cols="3">
                        <div class="quantity-container">
                          <v-btn style="color: #56B280;" class="quantity-btn" @click="diminuirCantidad(item.productId)">
                            -
                          </v-btn>
                          <p class="quantity-value">
                            {{ item.cantidad }}
                          </p>
                          <v-btn style="color: #56B280;" class="quantity-btn" @click="aumentarCantidad(item.productId)">
                            +
                          </v-btn>
                        </div>
                      </v-col>
                      <v-col cols="3">
                        <p style="color: #272727;" class="small-heading ">
                          {{ (item.cantidad * parseFloat(item.price.replace('$', ''))).toFixed(2) }}
                        </p>
                      </v-col>
                    </v-row>
                  </div>
                  <v-divider inset />
                  <v-row>
                    <v-col cols="6">
                      <p style="color: black;">
                        Sub-total:
                      </p>
                      <p style="color: #56B280;">
                        {{ totalPrice }}
                      </p>
                      <p class="small-heading" style="color: #272727;">
                        Tax and shipping cost will be calculated later
                      </p>
                    </v-col>
                    <v-col cols="6" class="text-right">
                      <router-link to="/details">
                        <v-btn color="#56B280" style="color: white;">
                          Check-out
                        </v-btn>
                      </router-link>
                    </v-col>
                  </v-row>
                </div>
              </v-card-text>
            </v-card>
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
      cart: []
    }
  },
  computed: {
    totalPrice () {
      return this.cart.reduce((total, item) => {
        return total + (item.cantidad * parseFloat(item.price.replace('$', '')))
      }, 0).toFixed(2)
    }
  },
  created () {
    this.loadCart()
  },
  methods: {
    loadCart () {
      const cart = JSON.parse(localStorage.getItem('cart')) || []
      this.cart = cart
    },
    aumentarCantidad (productId) {
      const item = this.cart.find(item => item.productId === productId)
      if (item) {
        item.cantidad++
        this.saveCart()
      }
    },
    diminuirCantidad (productId) {
      const item = this.cart.find(item => item.productId === productId)
      if (item && item.cantidad > 1) {
        item.cantidad--
        this.saveCart()
      }
    },
    removeItem (productId) {
      this.cart = this.cart.filter(item => item.productId !== productId)
      this.saveCart()
    },
    saveCart () {
      localStorage.setItem('cart', JSON.stringify(this.cart))
    }
  }
}
</script>
