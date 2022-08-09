<template>
  <div>
    <Banner />
    <div class="main-container">
      <h1>Monte seu Hambúrguer</h1>
    </div>
  </div>
</template>

<script>
import Banner from '@/components/Banner.vue';
// @ is an alias to /src


export default {
  name: 'HomeView',
  components: {
    Banner
}
}
</script>
