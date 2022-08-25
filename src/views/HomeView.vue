<template>
  <div>
    <Banner />
    <div class="main-container">
      <h1>Monte seu Hambúrguer</h1>
      <BurgerForm />
    </div>
  </div>
</template>


<script>
import Banner from '@/components/Banner.vue';
import BurgerForm from '@/components/BurgerForm.vue';
// @ is an alias to /src


export default {
  name: 'HomeView',
  components: {
    Banner,
    BurgerForm,
}
}
</script>
