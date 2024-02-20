<script lang="ts">
  import { getMonth } from "$lib/utils";
  import Button from "./Button.svelte";

  const { setOffset, offset } = $props<{
    offset: number;
    setOffset: (offset: number) => void;
  }>();

  const { month, year } = $derived(getMonth(offset as number));
</script>

<header>
  <h1 class="calendarMonth">
    {#each [...month] as [key]}
      <span>
        {key}
      </span>
    {/each}
  </h1>
  <h2 class="calendarYear">{year}</h2>

  <div>
    <Button onclick={() => setOffset(offset - 1)}>Prev</Button>

    <Button onclick={() => setOffset(0)} disabled={offset === 0}>Now</Button>

    <Button onclick={() => setOffset(offset + 1)}>Next</Button>
  </div>
</header>

<style>
  .calendarMonth {
    letter-spacing: -5px;
    font-size: 500%;
    margin-bottom: 0;
  }

  .calendarMonth span:nth-child(3) ~ span {
    display: none;
  }

  .calendarYear {
    letter-spacing: -2px;
    margin-top: 0;
    padding-bottom: 0.5em;
    border-bottom: 1px solid grey;
  }
</style>
