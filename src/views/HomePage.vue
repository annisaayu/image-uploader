<template>
  <div class="home">
  <div id="indexPage">
    <!-- <nav class="navbar is-fixed-top is-dark" role="navigation" aria-label="main navigation">
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
    </nav> -->
    <div class="columns">
      <div class="column is-4 is-offset-1">
        <form>
          <div class="field">
            <div class="control">
              <input class="input is-large" type="text" v-model="name" placeholder="Your name" autofocus="">
            </div>
          </div>

          <div class="field">
              <div class="control">
                  <input class="input is-large" type="email" v-model="email" placeholder="Your Email" autofocus="">
              </div>
          </div>
          <button class="button is-block is-info is-large is-fullwidth" @click="gettoken">Get Token</button>
        </form>
      </div>
      <div class="column is-4 is-offset-1">
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
          <a class="button" style="margin-left: 10px;" v-on:click="submitFile()">Post image</a>
        </div>
      </div>
    </div>
    

    <div class="free-collections section" >
      <div class="container">
        <div class="has-text-centered title">
          <h2>Find more images</h2>
        </div>

        <div class="columns collections-box">
          <!-- <ListImage
            v-for = "image in images"
            v-bind:image = "image"
            :key = "image.id"
          >
        </ListImage> -->
        
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
import axios from 'axios'

export default {
  name: 'homePage',
  data () {
    return {
      name: '',
      email:'',
      images:[],
      file: ''
    }
  },
  methods : {
    
    gettoken () {
      let self = this
      let account = {
        name: this.name,
        email: this.email
      }

      axios
          .post('http://35.197.135.159/request-token', account)
          .then(response => {
            let token = response.data.uuid
            localStorage.setItem('authorization', token) 
            axios
              .get('http://35.197.135.159/image',{
                headers: { Authorization: token }
              })
              .then(response => {
                self.images.push(response.data.images)
                console.log(self.images)
              })
              .catch(err => {
                  alert(err)
              })           
          })
    },
    
    uploadPhoto(event) {
      this.image = event.target.files[0]
    },

    submitFile () {
      let formData = new FormData();
      formData.append('photo', this.file);
      let token = localStorage.getItem('authorization')

      if(token) {
        if(this.file!=''){
							axios.post('http://35.197.135.159/image', formData, {
									headers: {
											authorization: token
									}
							}).then(response => {
									console.log(response)
							}).catch(err => {
									alert(err)
							})
            }
      }
    }
  }
}
</script>
