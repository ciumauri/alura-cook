<script>
  import Receita from "$lib/componentes/receitas/Receita.svelte";
  import Titulo from "$lib/componentes/compartilhados/Titulo.svelte";

  import receitas from "$lib/json/receitas.json";
  import { minhaLista } from "$lib/stores/minhaLista";
  import TagLink from "$lib/componentes/compartilhados/TagLink.svelte";

  $: receitasFiltradas = receitas.filter((receita) =>
    receita.ingredientes.every((ingrediente) =>
      $minhaLista.includes(ingrediente)
    )
  );
</script>

<svelte:head>
  <title>Alura Cook | Receitas</title>
</svelte:head>

<main>
  <Titulo tag="h1">Receitas</Titulo>

  <div class="info">
    <p class="verde">
      Resultados encontrados: <span class="numero"
        >{receitasFiltradas.length}</span
      >
    </p>
    {#if receitasFiltradas.length === 0}
      <p>
        Não encontramos nenhuma receita com os ingredientes que você tem por aí
        :(
      </p>
    {:else}
      <p>
        Veja as opções de receitas que encontramos com os ingredientes que você
        tem por aí!
      </p>
    {/if}
  </div>
  {#if receitasFiltradas.length}
    <div class="receitas">
      {#each receitasFiltradas as receita (receita.nome)}
        <Receita {receita} />
      {/each}
    </div>
  {/if}
  <div class="editar-lista">
    <TagLink href="/">Editar Lista</TagLink>
  </div>
</main>

<style>
  .info {
    margin-bottom: 3.375rem;
  }

  .info > p {
    line-height: 2rem;
  }

  .info > p.verde {
    color: var(--verde);
  }

  .receitas {
    text-align: start;
    margin-bottom: 3.75rem;

    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 1.5rem;
  }

  .editar-lista {
    display: flex;
    justify-content: center;
  }
</style>
