<template>
  <div class="container">
    <table class="table table-striped">
      <thead>
        <tr>
          <th scope="col">ID</th>
          <th class="text-center">Cliente</th>
          <th class="text-center">Pão</th>
          <th class="text-center">Carne</th>
          <th class="text-center">Opcionais</th>
          <th class="text-center">Ações</th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="burger in burgers" :key="burger.id">
          <th scope="row">{{ burger.id }}</th>
          <td class="text-center">{{ burger.nome }}</td>
          <td class="text-center">{{ burger.pao }}</td>
          <td class="text-center">{{ burger.carne }}</td>
          <td class="text-center">
            <span v-for="(opcional, index) in burger.opcionais" :key="index">
              {{ opcional }}/
            </span>
          </td>
          <td style="width: 150px">
            <select
              class="form-select form-select-sm"
              name="status"
              @change="updateBurger($event, burger.id)"
            >
              <option
                :value="s.tipo"
                v-for="s in status"
                :key="s.id"
                :selected="burger.status == s.tipo"
              >
                {{ s.tipo }}
              </option>
            </select>
          </td>
          <td class="d-flex justify-content-end">
            <button
              type="submit"
              class="btn btn-outline-dark btn-sm"
              @click="deleteBurger(burger.id)"
            >
              Cancelar
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "dashboard",
  data() {
    return {
      burgers: null,
      burger_id: null,
      status: [],
      msg: null,
    };
  },
  methods: {
    async getPedidos() {
      const req = await fetch("http://localhost:3000/burgers");

      const data = await req.json();

      this.burgers = data;

      // Resgata os status de pedidos
      this.getStatus();
    },
    async getStatus() {
      const req = await fetch("http://localhost:3000/status");

      const data = await req.json();

      this.status = data;
    },
    async deleteBurger(id) {
      const req = await fetch(`http://localhost:3000/burgers/${id}`, {
        method: "DELETE",
      });

      const res = await req.json();

      this.msg = "Pedido removido com sucesso!";

      // clear message
      setTimeout(() => (this.msg = ""), 3000);

      this.getPedidos();
    },
    async updateBurger(event, id) {
      const option = event.target.value;

      const dataJson = JSON.stringify({ status: option });

      const req = await fetch(`http://localhost:3000/burgers/${id}`, {
        method: "PATCH",
        headers: { "Content-Type": "application/json" },
        body: dataJson,
      });

      const res = await req.json();

      this.msg = "Pedido Nº ${res.id} foi atualizado para ${res.status}!";

      // clear message
      setTimeout(() => (this.msg = ""), 3000);

      console.log(res);
    },
  },
  mounted() {
    this.getPedidos();
  },
};
</script>

