<template>
  <div>
    <banner />
    <div>
      <h1 class="text-center pt-2">Monte o seu Hambúrguer:</h1>
      <burgerForm />
      <btnFlut />
    </div>
  </div>
</template>

<script>
import banner from "../components/Banner.vue";
import burgerForm from "../components/BurgerForm.vue";
import btnFlut from "../components/BtnFlutuante.vue";

export default {
  name: "home",
  components: {
    banner,
    burgerForm,
    btnFlut,
  },
};
</script>
