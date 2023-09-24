


<template>
    <div class="center-content">

        <form @submit.prevent="insereNome" >
            <input type="text" v-model="renderizaNome" placeholder="Insira sua tarefa aqui" />
            <input type="submit" value="Enivar">
        </form>
        <table class="content-table">
        <tr>
          <th>Tarefa</th>
          <th>Status</th>
          <th>Ações</th>
        </tr>
        <tr v-for="key in tarefa" :key="key">
            
          <td >{{ key }}</td>
          <td>
            <label>Concluido</label>
              <input type="checkbox" name="Concluido" id="concluido">
            <label>Pendente</label>
              <input type="checkbox" name="Concluido" id="pendente" ></td>
          <td>
            <form @submit.prevent="deletarTarefa" >
                <input type="button" value="Finalizar"  />
                <input type="button"  value="Deletar" v-on:click="deletarTarefa"  />
            </form>
          </td>
        </tr>
      </table>
    </div>
  </template>
  
  <script lang="ts">
  import { defineComponent } from 'vue';
  export default defineComponent({
    name: 'TabelaComponent',
    props: {
      msg: String,
    },
    data() {
      return {
        renderizaNome: '' ,
        insertName:'',
        tarefa:[]  as string [],
        cond: false
      };
    },
    methods: {
      insereNome() {
      this.insertName = this.renderizaNome
      const inputName = this.insertName.trim();
    
          if (typeof inputName === 'string' ) {
             this.tarefa.push(inputName);
             this.insertName = '';
             console.log(this.tarefa);
        }
   },
      finalizarTarefa() {
       //alsala
      },
      deletarTarefa() {
          this.tarefa.pop()
          this.cond = true
          console.log(this.tarefa)
      },
    },
  });
  </script>
<style>
.center-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: #cdf6eb;
  margin: 10px auto 30px;
  max-width: 100%;
  font-family: sans-serif;
  overflow-x: auto; 
}

.center-table {
  justify-content: center;
}

.content-table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 10px;
}

.content-table th {
  border: 1px solid #cccc;
}

.content-table tr {
  background-color: #f2f2f2;
}

/* Apply responsive font size */
@media (max-width: 600px) {
  .content-table th,
  .content-table td {
    padding: 8px 4px; /* Reduce cell padding for smaller screens */
    white-space: nowrap; /* Prevent text from wrapping in cells */
    overflow: hidden; /* Hide overflowing content */
    text-overflow: ellipsis; /* Show ellipsis (...) for overflowing content */
    font-size: 12px; /* Adjust font size based on your preference */
  }

  .content-table tr td:last-child {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .content-table tr td:last-child input[type="button"] {
    margin: 4px 0;
  }
}
</style>
