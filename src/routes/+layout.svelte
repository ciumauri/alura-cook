<script lang="ts">
  import "../app.css";

  import Cabecalho from "$lib/componentes/paginas/layout/Cabecalho.svelte";
  import MinhaLista from "$lib/componentes/paginas/layout/MinhaLista.svelte";
  import Rodape from "$lib/componentes/paginas/layout/Rodape.svelte";
  import { minhaLista } from "$lib/stores/minhaLista";
</script>

<div class="container-principal">
  <Cabecalho />
  <div class="estilo-principal">
    {#if $minhaLista.length > 0}
      <div class="minha-lista-container">
        <MinhaLista />
        <div class="divisoria" />
      </div>
    {/if}
    <slot><!-- optional fallback --></slot>
  </div>
  <Rodape />
</div>

<style>
  .container-principal {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
  }

  .estilo-principal {
    text-align: center;
    padding: 0 5vw 3.375rem;
    flex: 1;
  }

  .minha-lista-container {
    margin-bottom: 2rem;
  }

  .divisoria {
    width: 40vw;
    height: 2px;
    background-color: var(--verde);
    margin: 0 auto;
  }
</style>
