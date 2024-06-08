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
        <v-row class="d-flex align-stretch">
          <v-col cols="8">
            <v-card style="max-height: 530px;">
              <v-card-title>
                <h1 class="medium-m-heading" style="text-align: center;">
                  Shipping Address
                </h1>
              </v-card-title>
              <v-card-text>
                <v-form>
                  <v-row>
                    <v-col cols="6">
                      <v-text-field v-model="shippingInfo.name" label="Name" required />
                    </v-col>
                    <v-col cols="6">
                      <v-text-field v-model="shippingInfo.secondName" label="Second Name" />
                    </v-col>
                  </v-row>
                  <v-text-field v-model="shippingInfo.address" label="Address and number" required />
                  <v-text-field v-model="shippingInfo.note" label="Shipping note (optional)" />
                  <v-row>
                    <v-col cols="4">
                      <v-text-field v-model="shippingInfo.city" label="City" required />
                    </v-col>
                    <v-col cols="4">
                      <v-text-field v-model="shippingInfo.postalCode" label="Postal Code" required />
                    </v-col>
                    <v-col cols="4">
                      <v-select
                        v-model="shippingInfo.province"
                        :items="provinces"
                        label="Province"
                        required
                      />
                    </v-col>
                  </v-row>
                  <v-select
                    v-model="shippingInfo.country"
                    :items="countries"
                    label="Country/Region"
                    required
                  />
                  <v-checkbox
                    v-model="shippingInfo.saveForFuture"
                    label="Save this information for a future fast checkout"
                  />
                  <router-link to="/cart" class="text-decoration-none">
                    <v-btn text color="#56B280">
                      Back to cart
                    </v-btn>
                  </router-link>
                  <v-btn color="#56B280" class="white--text" @click="saveAndGoToShipping">
                    Go to shipping
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
                    <p>Calculated at the next step</p>
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
      shippingInfo: {
        name: '',
        secondName: '',
        address: '',
        note: '',
        city: '',
        postalCode: '',
        province: '',
        country: '',
        saveForFuture: false
      },
      countries: ['Italy', 'USA', 'Canada', 'UK', 'Germany'],
      provinces: ['Province 1', 'Province 2', 'Province 3']
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
    const savedShippingInfo = localStorage.getItem('shippingInfo')
    if (savedShippingInfo) {
    // Convertir la cadena JSON de vuelta a un objeto
      this.shippingInfo = JSON.parse(savedShippingInfo)
    }
  },
  methods: {
    loadCart () {
      const cart = JSON.parse(localStorage.getItem('cart')) || []
      this.cart = cart
    },
    saveShippingInfo () {
      const shippingInfo = JSON.stringify(this.shippingInfo)
      localStorage.setItem('shippingInfo', shippingInfo)
    },
    saveAndGoToShipping () {
      this.saveShippingInfo()
      this.goToShipping()
    },
    goToShipping () {
      this.$router.push({ name: 'shipping', query: { ...this.shippingInfo } })
    }
  }
}
</script>
