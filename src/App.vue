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
              />          <p style="color: red" v-for="error in errors" :key="error">
            {{ error }}
          </p>

            </div>
            <br />
            <!-- <button type="submit" class="btn btn-primary">Cadastrar</button> -->
            <button class="btn btn-primary" type="submit">Enviar</button>
          </form>
        </div>
        <!-- Tabela -->
        <div class="col-6">
          <br />
          <p>{{ nome }}</p>
          <p>{{ email }}</p>
          <p>{{ tel }}</p>
          <!-- <table border="1">
                   <tr class="text-center">
                       <th>nome</th>
                       <th>email</th>
                       <th>Telefone</th>
                   </tr>
                   <tr class="text-center">
                       <td>henriquepig@hotmail.com</td>
                       <td>123455*</td>
                       <td>(27) 99965-0933</td>
                   </tr>
               </table> -->
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      nome: "",
      email: "",
      tel: "",
      errors: [],
    };
  },
  methods: {      
    checkForm: function () {
        this.errors=[];
      if (this.nome === "") {
        this.errors.push("Campo Nome Obrigatorio");
      }
      if (this.email === "") {
        this.errors.push("Campo Email Obrigatorio");
      }
      if (this.tel === "") {
        this.errors.push("Campo Tel Obrigatorio");
      }
      if(this.nome&&this.email&&this.tel){
         alert("todos estão completos");
      }
    },
  },
};
</script>

<style>
.danger {
  border: 1px solid red !important;
}
</style>
