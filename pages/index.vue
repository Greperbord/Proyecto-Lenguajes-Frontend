<template>
  <v-app id="inspire">
    <v-main class="white">
      <v-img :src="require('@/assets/images/fondo1.jpg')">
        <div class="d-flex justify-center align-center" style="height: 100vh;">
          <div class="col-9 col-md-5" style="margin-top: 100px;">
            <v-card rounded :color="'rgba(255, 255, 255, 0.9)'" style="height: 50%!important;" elevation="0" max-width="600">
              <v-row style="max-height: 30px; max-width: 600px">
                <v-col>
                  <label>CORREO ELECTRÓNICO</label>
                  <v-row class="ma-2">
                    <v-icon style="margin-top: -25px">
                      mdi-email-outline
                    </v-icon>
                    <v-text-field v-model="email" style="margin-left: 20px !important; max-width: 600px;" rounded label="Ingresa tu correo" outlined />
                  </v-row>
                </v-col>
              </v-row>
              <v-row style="max-height: 130px; max-width: 600px; margin-top: 80px !important;">
                <v-col>
                  <label>CONTRASEÑA</label>
                  <v-row class="ma-2">
                    <v-icon style="margin-top: -25px">
                      mdi-account-outline
                    </v-icon>
                    <v-text-field
                      v-model="password"
                      style="margin-left: 20px !important; max-width: 600px;"
                      rounded
                      label="Ingresa tu contraseña"
                      type="password"
                      outlined
                    />
                  </v-row>
                </v-col>
              </v-row>

              <v-card-actions>
                <v-col cols="12">
                  <v-row align="center" style="max-width: 500px">
                    <a href="" style=" text-decoration: none !important; color: black;">
                      <v-icon>
                        mdi-account-outline
                      </v-icon>
                      <span style="font-size: 12px !important;">¿OLVIDASTE LA CONTRASEÑA?</span>
                    </a>
                  </v-row>
                  <v-row class="rowCard">
                    <v-btn block class="pa-2" color="#00e697" rounded @click="login">
                      <span style="text-transform: none; color: black;">INICIAR SESIÓN</span>
                    </v-btn>
                  </v-row>
                  <v-row class="rowCard">
                    <v-btn
                      block
                      class="pa-2"
                      style="margin-top: 20px;"
                      color="#00e697"
                      rounded
                      href="/register"
                    >
                      <span style="text-transform: none; color: black;">REGISTRARSE</span>
                    </v-btn>
                  </v-row>
                </v-col>
              </v-card-actions>
            </v-card>
          </div>
        </div>
      </v-img>
    </v-main>
  </v-app>
</template>

<script>
export default {
  auth: false,
  data () {
    return {
      email: null,
      password: null
    }
  },
  methods: {
    async login () {
      const sendData = {
        email: this.email,
        password: this.password
      }
      await this.$auth.loginWith('local', {
        data: sendData
      }).then(async (res) => {
        const result = await res.data
        if (result.message === 'success') {
          this.$store.commit('setToken', result.token)
          this.$router.push('/inicio')
        }
      }).catch((err) => {
        console.log('@@@ error => ', err)
      })
    }
  }
}
</script>
