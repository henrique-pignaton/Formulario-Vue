<template>
  <div id="app">
    <div class="container mt-5 col-12">
      <h1 class="mb-3 text-center branco">Cadastro de Usuario</h1>
      <div class="row">
        <!-- Formulario -->
        <div class="col-6">
          <form
            action=""
            class="branco"
            name="formulario"
            v-on:submit.prevent="checkForm"
          >
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
                v-mask="'(##)#####-####'"
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
        <div class="list-group branco col">
          <span class="text-center pt-3 branco" v-if="lista.length <= 0"
            >Sem Cadastros...</span
          >
          <table class="table branco" border="0">
            <tr class="text-center" v-if="lista.length > 0">
              <th>#id</th>
              <th>Nome</th>
              <th>Email</th>
              <th>Telefone</th>
            </tr>
            <tr
              class="text-center"
              v-for="(lista, index) in lista"
              :key="lista"
            >
              <td>{{ lista.id }}</td>
              <td>{{ lista.nome }}</td>
              <td>{{ lista.email }}</td>
              <td>{{ lista.tel }}</td>
              <td>
                <button
                  class="btn branco btn-custom btn-sm"
                  v-on:click.prevent="editarCadastro(index)"
                >
                  <i class="bi bi-pencil-square"></i> Editar
                </button>
              </td>
              <td>
                <button
                  href="#"
                  class="btn branco btn-custom btn-sm"
                  v-on:click.prevent="removercomentario(index)"
                >
                  <i class="bi bi-x-lg"></i> Excluir
                </button>
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
      lista: [{"nome":"Provident consequat","email":"xagatil@mailinator.com","tel":"(11)64977-1178","id":4},{"nome":"Laborum eligendi eos","email":"talyne@mailinator.com","tel":"(18)42784-9355","id":5},{"nome":"Quo corporis recusan","email":"gepys@mailinator.com","tel":"(16)92941-1788","id":10},{"nome":"Sed incidunt amet ","email":"xygabiba@mailinator.com","tel":"(18)28994-5456","id":11},{"nome":"Vero perferendis ips","email":"jati@mailinator.com","tel":"(16)97868-8662","id":12},{"nome":"Irure nisi proident","email":"cerog@mailinator.com","tel":"(14)04725-1794","id":13}],
      nome: "",
      email: "",
      tel: "",
      errors: [],
      id: 0,
      Editindex: "",
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
      if (this.nome!= ""&& this.email!="" && this.tel!="") {
        this.lista.push({
          nome: this.nome,
          email: this.email,
          tel: this.tel,
          id: this.id++,
        });
        this.nome = "";
        this.email = "";
        this.tel = "";
        this.Editindex=""
      }
    },
    removercomentario(index) {
      this.lista.splice(index, 1);
    },
    editarCadastro(index) {
      this.Editindex = [index];
      this.nome = this.lista[index].nome;
      this.email = this.lista[index].email;
      this.tel = this.lista[index].tel;
      console.log(Editindex);
    },if(Editindex)
  },
};
</script>

<style>
.danger {
  color: red !important;
}
body {
  background-color: rgb(46, 46, 46);
}
.branco {
  color: aliceblue;
}
input:focus {
  color: red;
}
@media (max-width: 992px) {
  body {
    align-items: center;
  }
  .col-6 {
    width: 100% !important;
  }
}
</style>
