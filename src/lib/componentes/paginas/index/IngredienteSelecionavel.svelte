<script lang="ts">
  import { minhaLista } from "$lib/stores/minhaLista";
  import Tag from "$lib/componentes/compartilhados/Tag.svelte";

  export let ingrediente: string;

  $: selecionado = $minhaLista.includes(ingrediente);

  function aoClicar() {
    if (!selecionado) {
      minhaLista.adicionarIngrediente(ingrediente);
    } else {
      minhaLista.removerIngrediente(ingrediente);
    }
  }
</script>

<button on:click={aoClicar}>
  <Tag active={selecionado}>
    {ingrediente}
  </Tag>
</button>

<style>
  button {
    cursor: pointer;
  }
</style>
