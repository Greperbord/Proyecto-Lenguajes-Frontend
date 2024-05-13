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
          <a style="color: black">Discovery</a>
          <a style="color: black">About</a>
          <a style="color: black">Contact us</a>
        </v-row>
      </v-container>
      <v-container>
        <v-row>
          <a style="position: absolute; right: 70px;" href="/">
            <v-img :src="require('@/assets/images/account.svg')" />
          </a>
          <a style="position: absolute; right: 20px;" href="/">
            <v-img :src="require('@/assets/images/cart.svg')" />
          </a>
        </v-row>
      </v-container>
    </v-app-bar>

    <v-main class="grey lighten-2">
      <v-container>
        <v-img :src="require('@/assets/images/fondo.svg')">
          <v-card color="#F7F8FACC" max-width="500" align="center">
            <v-title>
              <h1>🌱</h1>
            </v-title>
            <v-card-subtitle>
              <h1>The nature candle</h1>
            </v-card-subtitle>
            <v-card-text>All handmade with natural soy wax, Candleaf is a companion for all your pleasure moments.</v-card-text>
            <v-card-actions>
              <a href="">
                <v-img :src="require('@/assets/images/botonxd.svg')" />
              </a>
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
