<script lang="ts">
  export let active = false;
  export let tamanho: "md" | "lg" = "md";
  export let desabled = false;
</script>

<div class="tag {tamanho}" class:active class:desabled>
  <slot><!-- optional fallback --></slot>
</div>

<style>
  .tag {
    height: 48px;
    border-radius: 8px;
    padding: 1rem;
    text-align: center;
    color: var(--cor-texto-principal);
    background-color: var(--cinza);

    display: flex;
    justify-content: center;
    align-items: center;

    transition: all 0.2s ease-in-out;
  }

  .active {
    color: var(--branco);
    background-color: var(--laranja);
  }

  .lg {
    font-size: 1.125rem;
    padding: 1rem 1.25rem;
  }

  .desabled {
    opacity: 0.8;
    cursor: default;
  }
</style>
