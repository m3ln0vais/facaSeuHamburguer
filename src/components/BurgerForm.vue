<template>
  <div class="container d-flex justify-content-center">
    <form class="pt-2 pb-4" style="width: 350px">
      <div class="mb-3">
        <label for="nome" class="form-label border-start border-5 border-warning ps-2">Nome do cliente:</label>
        <input type="text" class="form-control" id="nome" />
      </div>

      <div class="mb-3">
        <label class="border-start border-5 border-warning ps-2 mb-2" for="pao">Escolha o pão:</label>
        <select
          class="form-select form-select-sm"
          aria-label="Default select example"
        >
          <option selected>Selecione o seu pão</option>
          <option value="1">One</option>
        </select>
      </div>

      <div class="mb-3">
        <label class="border-start border-5 border-warning ps-2 mb-2" for="carne">Escolha a carne do seu Burger:</label>
        <select
          class="form-select form-select-sm"
          aria-label="Default select example"
        >
          <option selected>Selecione o tipo de carne</option>
          <option value="1">One</option>
        </select>
      </div>

      <div id="opcionais-container">
        <label class="border-start border-5 border-warning ps-2 mb-2" id="opcionais-title" for="opcionais">
          Selecione os opcionais:
        </label>
        <div class="mb-3 form-check">
          <input type="checkbox" class="form-check-input" name="opcionais" />
          <label class="form-check-label" for="exampleCheck1">
            Check me out
          </label>
        </div>
      </div>
      <div class="d-grid gap-2">
        <button type="submit" class="btn btn-outline-dark btn-sm">
          Salvar Pedido
        </button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "burgerForm",
};
</script>