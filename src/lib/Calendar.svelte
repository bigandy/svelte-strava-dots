<script lang="ts">
  import Header from "./Header.svelte";
  import TableHeader from "./TableHeader.svelte";

  const { initialOffset } = $props<{
    initialOffset?: number;
  }>();
  let offset = $state(initialOffset ?? 0);

  const setOffset = (newOffset: number) => {
    offset = newOffset;
  };
</script>

<div class="wrapper">
  <Header {offset} {setOffset} />
  <table>
    <TableHeader />
    <!-- <TableBody {offset} {showDots} /> -->
  </table>
</div>

<style>
</style>
