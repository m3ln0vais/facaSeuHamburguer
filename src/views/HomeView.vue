<template>
  <div>
    <banner />
    <div>
      <h1 class="text-center pt-2">Monte o seu Hambúrguer:</h1>
      <burgerForm />
    </div>
  </div>
</template>

<script>
import banner from "../components/Banner.vue";
import burgerForm from "../components/BurgerForm.vue";

export default {
  name: "home",
  components: {
    banner,
    burgerForm,
  },
};
</script>