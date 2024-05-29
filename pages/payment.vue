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
      <v-container style="position: relative; top: 100px;">
        <v-row>
          <v-col cols="8">
            <v-card>
              <v-card-title>
                <h1 class="medium-m-heading" style="text-align: center;">
                  Payment details
                </h1>
              </v-card-title>
              <v-card-text>
                <v-form>
                  <v-row>
                    <v-col cols="12">
                      <v-text-field
                        v-model="contact"
                        label="Contact"
                        readonly
                      />
                    </v-col>
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
                      <v-text-field
                        v-model="shippingMethod"
                        label="Mehtod"
                        readonly
                      />
                    </v-col>
                  </v-row>

                  <v-row>
                    <v-col cols="12">
                      <h2 style="color: black">
                        Payment Method
                      </h2>
                      <v-card class=" elevation-1">
                        <v-card-title style="background-color: green;">
                          <v-icon style="color: black;">
                            mdi-credit-card-outline
                          </v-icon>
                          Credit card
                        </v-card-title>
                        <v-card-text>
                          <v-col>
                            <v-row class="ma-2">
                              <v-text-field
                                v-model="cardNumber"
                                label="card number"
                                outlined
                              />
                            </v-row>
                            <v-row class="ma-2">
                              <v-text-field
                                v-model="holderName"
                                label="holder namer"
                                outlined
                              />
                            </v-row>
                            <v-row class="ma-2">
                              <v-text-field
                                v-model="expiration"
                                label="expiration (MM/YY)"
                                outlined
                              />
                              <v-text-field
                                v-model="CVV"
                                label="CVV"
                                outlined
                              />
                            </v-row>
                          </v-col>
                        </v-card-text>
                      </v-card>
                    </v-col>
                  </v-row>

                  <v-row>
                    <v-col cols="12">
                      <h2 style="color: black">
                        Tax information
                      </h2>
                      <v-card class=" elevation-0">
                        <v-card-text>
                          <v-col>
                            <v-row class="ma-2">
                              <v-text-field
                                v-model="vatNumber"
                                label="vat number (optional)"
                                outlined
                              />
                            </v-row>
                            <v-row class="ma-2">
                              <v-text-field
                                v-model="pec"
                                label="PEC (optional)"
                                outlined
                              />
                            </v-row>
                          </v-col>
                        </v-card-text>
                      </v-card>
                    </v-col>
                  </v-row>

                  <v-row>
                    <v-col cols="12">
                      <h2 style="color: black">
                        Billing Adress
                      </h2>
                      <v-card class=" elevation-0">
                        <v-radio-group v-model="selectedOption">
                          <v-radio label="Same as the shipping adress" value="opcionA" />
                        </v-radio-group>
                      </v-card>
                    </v-col>
                  </v-row>

                  <router-link to="/shipping" class="text-decoration-none">
                    <v-btn text color="#56B280">
                      Back to shipping
                    </v-btn>
                  </router-link>
                  <v-btn color="#56B280" class="white--text" @click="Paynow">
                    Pay now
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
