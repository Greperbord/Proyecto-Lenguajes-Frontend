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
      <v-container>
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
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: 'IndexPage',
  auth: false
}
</script>
