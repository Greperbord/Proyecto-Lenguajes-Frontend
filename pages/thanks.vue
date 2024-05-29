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
    </v-app-bar>

    <v-main class="grey lighten-2">
      <v-container style="position: relative; top: 100px;">
        <v-row>
          <v-col cols="8">
            <v-card>
              <v-card-title>
                <h1 class="medium-m-heading" style="text-align: center;">
                  Payment details
                </h1>
              </v-card-title>
              <v-card-subtitle class="text-center">
                <v-img :src="require('@/assets/images/check.svg')" style="max-width: 100px; max-height: 100px; margin-left: 43%;" />
                <h2 style="color: black">
                  Payment confirmed
                </h2>
                <h3 style="color: rgba(86, 178, 128, 1);">
                  ORDER #23039
                </h3>
              </v-card-subtitle>
              <v-card-text class="text-center">
                Thank you for buying Candleaf. The nature is grateful to you. Now that your order is confirmed it will be ready to ship in 2 days. Please check your inbox in the future for your order updates.
              </v-card-text>
              <v-card-actions>
                <v-col>
                  <v-row justify="center" align="center">
                    <v-btn style="background-color: rgba(86, 178, 128, 1); color: white">
                      <a href="/inicio" style="text-decoration: none; color: white;">
                        <span>Back to shopping</span>
                      </a>
                    </v-btn>
                  </v-row>
                  <v-row justify="center" align="center">
                    <a href="" style="color: rgba(86, 178, 128, 1); margin-top: 16px;">
                      Print receipt
                    </a>
                  </v-row>
                </v-col>
              </v-card-actions>
            </v-card>
          </v-col>

          <v-col cols="4">
            <v-card>
              <v-card-title>
                <h2 class="medium-m-heading">
                  Summary
                </h2>
              </v-card-title>
              <v-card-text>
                <div v-for="item in cart" :key="item.productId">
                  <v-row>
                    <v-col cols="3">
                      <v-img :src="require(`@/assets/images/${item.image}`)" />
                    </v-col>
                    <v-col cols="9">
                      <p>{{ item.name }}</p>
                      <p>{{ item.price }}</p>
                    </v-col>
                  </v-row>
                </div>
                <v-divider />
                <v-row>
                  <v-col cols="6">
                    <p>Subtotal</p>
                  </v-col>
                  <v-col cols="6">
                    <p>{{ totalPrice }}</p>
                  </v-col>
                </v-row>
                <v-row>
                  <v-col cols="6">
                    <p>Shipping</p>
                  </v-col>
                  <v-col cols="6">
                    <p>Free Shipping</p>
                  </v-col>
                </v-row>
                <v-row>
                  <v-col cols="6">
                    <p>Total</p>
                  </v-col>
                  <v-col cols="6">
                    <p>{{ totalPrice }}</p>
                  </v-col>
                </v-row>
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
      cart: [],
      contact: 'zzz',
      shippingAddress: '',
      shippingMethod: 'Standard',
      selectedOption: null
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
    this.loadShippingInfo()
  },
  methods: {
    loadCart () {
      const cart = JSON.parse(localStorage.getItem('cart')) || []
      this.cart = cart
    },
    loadShippingInfo () {
      const shippingInfo = JSON.parse(localStorage.getItem('shippingInfo')) || []
      this.shippingInfo = shippingInfo
      const { city, postalCode, province, country } = this.shippingInfo
      this.shippingAddress = `${city}, ${postalCode}, ${province}, ${country}`
    },
    Paynow () {
      // Navegar a la página de thanks.
      this.$router.push('/thanks')
    }
  }
}
</script>

<style scoped>
.text-decoration-none {
  text-decoration: none;
}
</style>
