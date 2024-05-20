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
      <v-container style="position: relative; top: 100px;">
        <v-row>
          <v-col cols="12">
            <v-card>
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
                      <p style="color: #272727;">
                        Product
                      </p>
                    </v-col>
                    <v-col cols="3">
                      <p style="color: #272727;">
                        Price
                      </p>
                    </v-col>
                    <v-col cols="3">
                      <p style="color: #272727">
                        Quantity
                      </p>
                    </v-col>
                    <v-col cols="3">
                      <p style="color: #272727;">
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
                        <p>{{ item.price }}</p>
                      </v-col>
                      <v-col cols="3">
                        <v-btn elevation="2" x-small @click="diminuirCantidad(item.productId)">
                          <v-icon>
                            mdi-minus
                          </v-icon>
                        </v-btn>
                        <p style="margin: 0 10px; color: #272727;">
                          {{ item.cantidad }}
                        </p>
                        <v-btn elevation="2" x-small @click="aumentarCantidad(item.productId)">
                          <v-icon>
                            mdi-plus
                          </v-icon>
                        </v-btn>
                      </v-col>
                      <v-col cols="3">
                        <p style="color: #272727;">
                          {{ totalPrice }}
                        </p>
                      </v-col>
                    </v-row>
                  </div>
                  <v-divider inset />
                  <v-row>
                    <v-col cols="6">
                      <p style="color: black;">
                        Subtotal:
                      </p>
                      <p style="color: #56B280;">
                        {{ totalPrice }}
                      </p>
                      <p>
                        Tax and shipping cost will be calculated later
                      </p>
                    </v-col>
                    <v-col cols="6" class="text-right">
                      <v-btn color="#56B280" style="color: white;">
                        Check-Out
                      </v-btn>
                    </v-col>
                  </v-row>
                </div>
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
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
