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
          <router-link to="/productos" style="text-decoration: none;">
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
      <div style="background-color: aqua;">
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
      </div>

      <div style="text-align: center; background-color: white;">
        <h2 style="color: #0B254B;">
          Products
        </h2>
        <p style="color: #5E6E89;">
          Order it for you or for your beloved ones
        </p>
        <div class="products">
          <a href="`/productos/${product.id}`">
            <div class="product-card">
              <div class="product-background">
                <img :src="require('/assets/images/product1.svg')">
              </div>
              <div class="product-card-footer">
                <h4>Spiced Mint</h4>
                <p>$12.56</p>
              </div>
            </div>
          </a>
          <a href="/item2">
            <div class="product-card">
              <div class="product-background">
                <img :src="require('/assets/images/product2.svg')">
              </div>
              <div class="product-card-footer">
                <h4>Sweet Strawberry</h4>
                <p>$9.99</p>
              </div>
            </div>
          </a>
          <a href="/item3">
            <div class="product-card">
              <div class="product-background">
                <img :src="require('/assets/images/product3.svg')">
              </div>
              <div class="product-card-footer">
                <h4>Cool Blueberris</h4>
                <p>$9.99</p>
              </div>
            </div>
          </a>
          <a href="/item4">
            <div class="product-card">
              <div class="product-background">
                <img :src="require('/assets/images/product4.svg')">
              </div>
              <div class="product-card-footer">
                <h4>Juicy Lemon</h4>
                <p>$9.99</p>
              </div>
            </div>
          </a>
          <a href="/item5">
            <div class="product-card">
              <div class="product-background">
                <img :src="require('/assets/images/product5.svg')">
              </div>
              <div class="product-card-footer">
                <h4>Stary Golden</h4>
                <p>$9.99</p>
              </div>
            </div>
          </a>
          <a href="/item6">
            <div class="product-card">
              <div class="product-background">
                <img :src="require('/assets/images/product6.svg')">
              </div>
              <div class="product-card-footer">
                <h4>Fragrant Cinnamon</h4>
                <p>$9.99</p>
              </div>
            </div>
          </a>
          <a href="/item7">
            <div class="product-card">
              <div class="product-background">
                <img :src="require('/assets/images/product7.svg')">
              </div>
              <div class="product-card-footer">
                <h4>Summer Cherrys</h4>
                <p>$9.99</p>
              </div>
            </div>
          </a>
          <a href="/item8">
            <div class="product-card">
              <div class="product-background">
                <img :src="require('/assets/images/product8.svg')">
              </div>
              <div class="product-card-footer">
                <h4>Clean Lavander</h4>
                <p>$9.99</p>
              </div>
            </div>
          </a>
        </div>
      </div>

      <div style="background-color: #F7F8FA; align-items: center; display: flex; justify-content: space-between; margin: 0 auto; flex-wrap: wrap-reverse;">
        <div style="margin-bottom: 20px;  margin-left: 150px;">
          <h1>Clean and fragrant soy wax</h1>
          <p style="color: #56B280;">
            Made for your home and for your wellness
          </p>
          <div>
            <p>
              <v-icon>mdi-check-circle-outline</v-icon>
              Eco-sustainable:All recyclable materials, 0% CO2 emissions.
            </p>
            <p>
              <v-icon>mdi-check-circle-outline</v-icon>
              Hyphoallergenic: 100% natural, human friendly ingredients.
            </p>
            <p>
              <v-icon>mdi-check-circle-outline</v-icon>
              Handmade: All candles are craftly made with love.
            </p>
            <p>
              <v-icon>mdi-check-circle-outline</v-icon>
              Long burning: No more waste. Created for last long.
            </p>
          </div>
          <button class="learn-more">
            Learn more
          </button>
        </div>
        <div style="overflow-clip-margin: content-box; overflow: clip; margin-right: 150px;">
          <v-img :src="require('@/assets/images/promotion-img.svg')" />
        </div>
      </div>

      <div class="testimonial">
        <h1>Testimonials</h1>
        <p>Some quotes from our happy customers</p>
        <div class="testimonials">
          <div class="testimonial-card">
            <div style="text-align: center;">
              <div class="avatar">
                <v-img :src="require('@/assets/images/Luisa.svg')" />
              </div>
              <div>
                <span>
                  <v-img :src="require('@/assets/images/star1.svg')" />
                </span>
              </div>
              <p>"“I love it! No more air fresheners”"</p>
              <span style="color: #7c8087; font-size: 18px;">Luisa</span>
            </div>
          </div>
          <div class="testimonial-card">
            <div style="text-align: center;">
              <div class="avatar">
                <v-img :src="require('@/assets/images/Edoardo.svg')" />
              </div>
              <div>
                <span>
                  <v-img :src="require('@/assets/images/star2.svg')" />
                </span>
              </div>
              <p>"Reccomended for everyone"</p>
              <span style="color: #7c8087; font-size: 18px;">Edoardo</span>
            </div>
          </div>
          <div class="testimonial-card">
            <div style="text-align: center;">
              <div class="avatar">
                <v-img :src="require('@/assets/images/Mart.svg')" />
              </div>
              <div>
                <span class="star">
                  <v-img :src="require('@/assets/images/star2.svg')" />
                </span>
              </div>
              <p>"“Looks very natural, the smell is awesome!“"</p>
              <span style="color: #7c8087; font-size: 18px;">Mart</span>
            </div>
          </div>
        </div>
      </div>

      <div class="popular-product">
        <h3>Popular</h3>
        <p>Our top selling product that you may like</p>
        <div class="products" style="">
          <a href="/item1">
            <div class="product-card">
              <div class="product-background">
                <img :src="require('/assets/images/product1.svg')">
              </div>
              <div class="product-card-footer">
                <h4>Spiced Mint</h4>
                <p>$12.56</p>
              </div>
            </div>
          </a>
          <a href="/item2">
            <div class="product-card">
              <div class="product-background">
                <img :src="require('/assets/images/product2.svg')">
              </div>
              <div class="product-card-footer">
                <h4>Sweet Strawberry</h4>
                <p>$9.99</p>
              </div>
            </div>
          </a>
          <a href="/item3">
            <div class="product-card">
              <div class="product-background">
                <img :src="require('/assets/images/product3.svg')">
              </div>
              <div class="product-card-footer">
                <h4>Cool Blueberris</h4>
                <p>$9.99</p>
              </div>
            </div>
          </a>
          <a href="/item4">
            <div class="product-card">
              <div class="product-background">
                <img :src="require('/assets/images/product4.svg')">
              </div>
              <div class="product-card-footer">
                <h4>Juicy Lemon</h4>
                <p>$9.99</p>
              </div>
            </div>
          </a>
        </div>
      </div>

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
  name: 'IndexPage',
  auth: false
}
</script>

<style scoped>
.products {
  margin-left: 130px;
  grid-gap: 18px;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  width: 80%;
}

.product-card {
  border-radius: 5px;
    cursor: pointer;
    display: flex;
    flex-direction: column;
    height: 230px;
    transition: all .3s ease-in-out;
}

.product-background {
    background-color: #f7f8fa;
    border-top-left-radius: 5px;
    border-top-right-radius: 5px;
    height: 152px;
    margin-bottom: 0;
    width: 100%;
}

.product-card-footer {
    background-color: #fff;
    border-bottom-left-radius: 5px;
    border-bottom-right-radius: 5px;
    height: 76px;
}
.learn-more {
    background-color:#56B280;
    border: 1px solid transparent;
    border-radius: 4px;
    color: #fff;
    margin-top: 10px;
    padding: 8px 44px;
}
.testimonial {
    margin: 45px auto;
    text-align: center;
    width: 85%;
    align-items: center;
}
.testimonials {
    grid-gap: 18px;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    margin-bottom: 35px;
    margin-top: 35px;
}
.testimonial-card {
    align-items: center;
    background-color: #fff;
    border-radius: 6px;
    display: flex;
    height: 380px;
    justify-content: center;
}
.avatar {
  width: 250px;
  height: 220px;
  top: 10px;
  opacity: 0px;
  margin-top: -100px;
  margin-left: 20px;
}
.star {
  width: 145.95px;
  height: 24px;
  top: 131px;
  left: 102px;
  gap: 0px;
  opacity: 0px;
}
.popular-product {
    margin: 45px auto;
    text-align: center;
    align-items: center;
    background-color: white;
}
.footer {
  align-items: center;
  background-color: black;
  display: flex;
  height: auto;
  justify-content: center;
}
.footer-wrapper {
  margin: 45px auto;
  width: 85%;
}
.footer-content {
  display: block;
}
.footer-links {
    display: flex;
    flex: 1 1;
    gap: 35px;
    justify-content: flex-end;
}
.links-wrapper {
    display: flex;
    flex-direction: column;
}
.links {
    display: flex;
    flex-direction: column;
    gap: 15px;
}

</style>
