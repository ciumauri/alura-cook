<script lang="ts">
  import Titulo from "$lib/componentes/compartilhados/Titulo.svelte";
  import Categoria from "$lib/componentes/paginas/index/Categoria.svelte";

  import categorias from "$lib/json/categorias.json";

  import { minhaLista } from "$lib/stores/minhaLista";
  import { beforeNavigate } from "$app/navigation";
  import TagLink from "$lib/componentes/compartilhados/TagLink.svelte";

  $: ifListIsEmpty = $minhaLista.length === 0;

  beforeNavigate((navigation) => {
    if (ifListIsEmpty && navigation.to?.url.pathname === "/receitas") {
      alert(
        "Você precisa selecionar pelo menos um ingrediente para buscar suas receitas!"
      );
      return navigation.cancel();
    }
  });
</script>

<svelte:head>
  <title>Alura Cook</title>
</svelte:head>

<main>
  <Titulo tag="h1">Ingredientes</Titulo>
  <div class="info">
    <p>Selecione abaixo os ingredientes que você deseja usar nesta refeição:</p>
    <p>*Atenção: consideramos que você tenha em casa sal, pimenta e água.</p>
  </div>

  <ul class="categorias">
    {#each categorias as categoria (categoria.nome)}
      <li>
        <Categoria {categoria} />
      </li>
    {/each}
  </ul>

  <div class="buscar-receitas">
    <TagLink href="/receitas" desabled={ifListIsEmpty}>Buscar Receitas</TagLink>
  </div>
</main>

<style>
  .info {
    margin-bottom: 3.375rem;
  }

  .info > p {
    line-height: 2rem;
  }

  .categorias {
    margin-bottom: 4.6875rem;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 1.5rem;
  }

  .buscar-receitas {
    display: flex;
    justify-content: center;
  }
</style>
