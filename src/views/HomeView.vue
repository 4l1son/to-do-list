<template>
  <div class="home">
    
    <img alt="Vue logo" src="../assets/logo.png" />
    <TabelaComponent />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import TabelaComponent from '@/components/TabelaComponent.vue';

export default defineComponent({
  name: 'HomeView',
  
  components: {
    TabelaComponent,
  },
  data() {
    return {
      renderizaNome:'' , 
    };
  },
  methods: {
    insereNome() {
      alert("Tarefa cadastrada com sucesso!") 
    },
  },
});
</script>
