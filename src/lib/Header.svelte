<script lang="ts">
  import { getMonth } from "./utils";

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
    <button onclick={() => setOffset(offset - 1)}> Prev </button>

    <button onclick={() => setOffset(0)}> Now </button>

    <button onclick={() => setOffset(offset + 1)}> Next </button>
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
