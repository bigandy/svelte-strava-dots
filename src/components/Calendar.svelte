<script lang="ts">
  import Header from "./Header.svelte";
  import TableHeader from "./TableHeader.svelte";
  import TableBody from "./TableBody.svelte";

  interface Props {
    initialOffset?: number;
  }

  const { initialOffset } = $props<Props>();

  let offset = $state(initialOffset ?? 0);

  const setOffset = (newOffset: number) => {
    offset = newOffset;
  };
</script>

<div class="wrapper">
  <Header {offset} {setOffset} />
  <table>
    <TableHeader />
    <TableBody {offset} />
  </table>
</div>
