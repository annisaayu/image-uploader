<template>
  <div class="home">
      <div id="indexPage">
    <nav class="navbar is-fixed-top is-dark" role="navigation" aria-label="main navigation">
      <div class="navbar-brand">
        <a class="navbar-item logo" href="#">
          UIStock
        </a>
      </div>
      <div class="navbar-menu">
        <div class="navbar-start">
          <a class="navbar-item is-tab is-active">Home</a>
        </div>
      </div>
    </nav>

    <div class="column is-4 is-offset-4">
      <form>
        <div class="field">
            <div class="control">
                <input class="input is-large" type="email" placeholder="Your Email" autofocus="">
            </div>
        </div>

        <div class="field">
            <div class="control">
                <input class="input is-large" type="password" placeholder="Your Password">
            </div>
        </div>
        <div class="field">
          <label class="checkbox">
            <input type="checkbox">
            Remember me
          </label>
        </div>
        <button class="button is-block is-info is-large is-fullwidth">Login</button>
      </form>
    </div>

    <div class="free-collections section" >
      <div class="container">
        <div class="has-text-centered title">
          <h2>Find more images</h2>
        </div>

        <div class="file has-name" style="margin:10px;">
          <label class="file-label">
            <input class="file-input" type="file" name="resume" v-on:change="uploadPhoto()">
            <span class="file-cta">
              <span class="file-icon">
                <i class="fas fa-upload"></i>
              </span>
              <span class="file-label">
                Choose a file…
              </span>
            </span>
            <span class="file-name">

            </span>
          </label>
          <a class="button" style="margin-left: 10px;">Button</a>
        </div>

        <div class="columns collections-box">
          <ListImage
            v-for = "image in images"
            v-bind:image = "image"
            :key = "image.id"
          >
        </ListImage>
        </div>
      </div>
    </div>

    <footer class="has-background-grey-darker">
      <div class="container has-text-centered has-text-white">
        &copy; 2018 Live Code | Annisa Ayu Pertiwi
      </div>
    </footer>
  </div>
  </div>
</template>

<script>
// import ListImage from '@/components/ListImage.vue'

export default {
  name: 'homePage',
  components : {
    ListImage
  },
  data () {
    return {
      images : [
      {
        id: 1,
        image: './assets/images/plant-photography-fruit-leaf-flower-orange-928361-pxhere.com.jpg',
        title: 'Fruit Leaf Flower Orange',
        price: '120000'
      }, {
        id: 2,
        image: './assets/images/amazing-autumn-dawn-131723.jpg',
        title: 'Autumn Dawn',
        price: '100000'
      }, {
        id: 3,
        image: './assets/images/person-people-girl-woman-photography-female-1387835-pxhere.com.jpg',
        title: 'Beauty Pink',
        price: '80000'
      }, {
        id: 4,
        image: './assets/images/snow-winter-warm-sweet-morning-cup-648807-pxhere.com.jpg',
        title: 'Winter Warm',
        price: '130000'
      }
    ]
    }
  }
}
</script>
