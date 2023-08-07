<template>
  <div class="container d-flex justify-content-center">
    <form
      class="pt-2 pb-4"
      style="width: 350px"
      method="POST"
      @submit.prevent="createBurger"
      novalidate
    >
      <div class="mb-3">
        <label for="nome" class="form-label border-start border-5 border-warning ps-2">
          Nome do cliente:
        </label>
        <input
          type="text"
          class="form-control"
          id="nome"
          name="nome"
          v-model="nome"
          required="required"
        />
        <div class="invalid-feedback">Insira um nome</div>
      </div>

      <div class="mb-3">
        <label class="border-start border-5 border-warning ps-2 mb-2" for="pao">
          Escolha o pão:
        </label>
        <select
          class="form-select form-select-sm"
          name="pao"
          id="pao"
          v-model="pao"
          required="required"
        >
          <option v-for="pao in paes" :key="pao.id" :value="pao.tipo">
            {{ pao.tipo }}
          </option>
        </select>
        <div class="invalid-feedback">Selecione um tipo de pão</div>
      </div>

      <div class="mb-3">
        <label class="border-start border-5 border-warning ps-2 mb-2" for="carne">
          Escolha a carne do seu Hambúrguer:
        </label>
        <select
          class="form-select form-select-sm"
          aria-label="Default select example"
          name="carne"
          id="carne"
          v-model="carne"
          required="required"
        >
          <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">
            {{ carne.tipo }}
          </option>
        </select>
        <div class="invalid-feedback">Selecione um tipo de carne</div>
      </div>

      <div id="opcionais-container">
        <label
          class="border-start border-5 border-warning ps-2 mb-2"
          id="opcionais-title"
          for="opcionais"
        >
          Selecione os opcionais:
        </label>
        <div class="mb-3 form-check" v-for="opcional in opcionaisdata" :key="opcional.id">
          <input
            type="checkbox"
            class="form-check-input"
            name="opcionais"
            v-model="opcionais"
            :value="opcional.tipo"
          />
          <label class="form-check-label" for="opcionais">
            {{ opcional.tipo }}
          </label>
        </div>
      </div>

      <div class="d-grid gap-2">
        <button type="submit" class="btn btn-outline-dark btn-sm">Salvar Pedido</button>
      </div>
    </form>
  </div>
</template>

<script>
import $ from "jquery";

export default {
  name: "burgerForm",
  data() {
    return {
      paes: null,
      carnes: null,
      opcionaisdata: null,
      nome: null,
      pao: null,
      carne: null,
      opcionais: [],
      status: "Solicitado",
      msg: null,
    };
  },
  methods: {
    async getIngredientes() {
      const req = await fetch("http://localhost:3000/ingredientes");
      const data = await req.json();
      // console.log(data);

      this.paes = data.paes;
      this.carnes = data.carnes;
      this.opcionaisdata = data.opcionais;
    },
    // enviarForm(){
    //   console.log('a');
    //   this.createBurger()
    // },
    async createBurger(e) {
      // console.log(e.target);
      if ($("#nome").val() === "" || $("#pao").val() === null || $("#carne").val() === null) {
        e.target.classList.add("was-validated");
      } else {
        const data = {
          nome: this.nome,
          carne: this.carne,
          pao: this.pao,
          opcionais: Array.from(this.opcionais),
          status: "Solicitado",
        };

        const dataJson = JSON.stringify(data);

        const req = await fetch("http://localhost:3000/burgers", {
          method: "POST",
          headers: { "Content-Type": "application/json" },
          body: dataJson,
        });

        const res = await req.json();

        console.log(res);

        this.nome = "";
        this.carne = "";
        this.pao = "";
        this.opcionais = [];
        e.target.classList.remove("was-validated");
      }
    },
  },
  mounted() {
    this.getIngredientes();
  },
};
</script>
