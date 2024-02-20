<script lang="ts">
  interface Props {
    onclick: any;
    children: any;
    disabled?: boolean;
  }
  const { children, ...props } = $props<Props>();
</script>

<button {...props}>
    {@render children()}
</button>

<style>
    button {
        padding: 0.5rem 0.75rem;
    }
</style>