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
    </v-app-bar>

    <v-main class="grey lighten-2">
      <v-container style="position: relative; top: 50px;">
        <v-row>
          <v-col cols="8">
            <v-card>
              <v-card-title>
                <h1 class="medium-m-heading" style="text-align: center;">
                  Shipping Details
                </h1>
              </v-card-title>
              <v-card-text>
                <v-form>
                  <v-row>
                    <v-col cols="12">
                      <v-text-field
                        v-model="shippingAddress"
                        label="Ship to"
                        readonly
                      />
                    </v-col>
                  </v-row>
                  <v-row>
                    <v-col cols="12">
                      <h2>Shipping method</h2>
                      <v-radio-group v-model="shippingMethod">
                        <v-radio label="Standard Shipping" value="standard" />
                      </v-radio-group>
                      <p>Free</p>
                    </v-col>
                  </v-row>
                  <router-link to="/details" class="text-decoration-none">
                    <v-btn text color="#56B280">
                      Back to details
                    </v-btn>
                  </router-link>
                  <v-btn color="#56B280" class="white--text" @click="goToPayment">
                    Go to payment
                  </v-btn>
                </v-form>
              </v-card-text>
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
                <v-text-field label="Coupon code" outlined />
                <v-btn outlined color="#56B280">
                  Add code
                </v-btn>
                <v-row style="margin-top: 10px;">
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
      shippingInfo: [],
      shippingAddress: '',
      shippingMethod: 'standard'
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
      const { city, postalCode, province, country } = this.$route.query
      this.shippingAddress = `${city}, ${postalCode}, ${province}, ${country}`
    },
    goToPayment () {
      this.$router.push({ name: 'payment' })
    }
  }
}
</script>

<style scoped>
.text-decoration-none {
  text-decoration: none;
}
</style>
