<script lang="ts">
  import Tag from "./Tag.svelte";

  export let href: string;
  export let desabled = false;
</script>

<a {href}>
  <Tag active={true} tamanho="lg" {desabled}
    ><slot><!-- optional fallback --></slot></Tag
  >
</a>
