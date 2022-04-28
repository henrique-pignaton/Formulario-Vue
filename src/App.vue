<template>
  <div id="app">
    <div class="container mt-5 col-12">
      <h1 class="mb-3 text-center">Cadastro de Usuario</h1>
      <div class="row">
        <!-- Formulario -->
        <div class="col-6">
          <form action="" name="formulario" v-on:submit.prevent="checkForm">
            <div class="form-group">
              <label for="nome">Nome:</label>
              <input
                name="nome"
                type="text"
                id="nome"
                class="form-control"
                placeholder="Seu nome"
                v-model="nome"
              />
            </div>
            <br />
            <div class="form-group">
              <label for="email">Email:</label>
              <input
                name="email"
                type="text"
                class="form-control"
                placeholder="Sua email"
                v-model="email"
              />
            </div>
            <br />
            <div class="form-group">
              <label for="">Numero de Telefone:</label>
              <input
                name="tel"
                type="tel"
                class="form-control"
                placeholder="Seu Telefone"
                v-model="tel"
                v-mask="'(##)9####-####'"
              />
              <p class="danger" v-for="error in errors" :key="error">
                {{ error }}
              </p>
            </div>
            <br />
            <button class="btn btn-primary" type="submit">Enviar</button>
          </form>
        </div>
        <!-- Tabela -->
        <div class="list-group col">
          <span class="text-center pt-3" v-if="lista.length <= 0"
            >Sem Cadastros...</span
          >
          <table class="table" border="0">
            <tr class="text-center" v-if="lista.length > 0">
              <th>Nome</th>
              <th>Email</th>
              <th>Telefone</th>
              <th></th>
              <th></th>
            </tr>
            <tr
              class="text-center"
              v-for="(lista, index) in allComments"
              :key="lista"
            >
              <td>{{ lista.nome }}</td>
              <td>{{ lista.email }}</td>
              <td>{{ lista.tel }}</td>
              <td>
                <button class="btn btn-custom btn-sm">
                  <i class="bi bi-pencil-square"></i> Editar
                </button>
              </td>
              <td>
                <a
                  href="#"
                  class="btn btn-custom btn-sm"
                  v-on:click.prevent="removeComment(index)"
                  ><i class="bi bi-x-lg"></i> Excluir</a
                >
              </td>
            </tr>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      lista: [],
      nome: "",
      email: "",
      tel: "",
      errors: [],
    };
  },
  methods: {
    checkForm: function () {
      this.errors = [];
      if (this.nome === "") {
        this.errors.push("Campo Nome Obrigatorio");
      }
      if (this.email === "") {
        this.errors.push("Campo Email Obrigatorio");
      }
      if (this.tel === "") {
        this.errors.push("Campo Tel Obrigatorio");
      }
      if (this.nome && this.email && this.tel) {
        this.lista.push({
          nome: this.nome,
          email: this.email,
          tel: this.tel,
        });
        this.nome = "";
        this.email = "";
        this.tel = "";
      }
    },
    removeComment(index) {
      console.log(index);
      this.lista.splice(index, 1);
    },
  },
  computed: {
    allComments() {
      return this.lista.map((lista) => ({
        ...lista,
      }));
    },
  },
};
</script>

<style>
.danger {
  color: red !important;
}
</style>
