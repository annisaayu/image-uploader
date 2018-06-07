<template>
  <div class="card-image">
    <div class="box">
      <figure class="image is-4by3">
        <img v-bind:src="image.image">
      </figure>
      <div class="content has-text-centered">
        <a href="#" class="is-size-5 has-text-centered has-text-grey-darker" > {{ image.title }} </a>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  props: ['image'],
  name: 'ListImage',
}
</script>
