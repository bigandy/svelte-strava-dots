<script lang="ts">
  import { getMonth } from "./utils";
  import Cell from "./Cell.svelte";

  interface Props {
    offset: number;
    showDots?: boolean;
  }

  const { offset, showDots } = $props<Props>();

  const { daysInMonth, firstDayofMonth, todayDay } = $derived(getMonth(offset));
  const rows = $derived(Math.ceil((daysInMonth + firstDayofMonth) / 7));
</script>

<tbody>
  {#each [...new Array(rows)] as _, rowIndex}
    <tr>
      {#each [...new Array(7)] as _, columnIndex}
        <Cell
          {rowIndex}
          {columnIndex}
          {firstDayofMonth}
          {todayDay}
          {daysInMonth}
        />
      {/each}
    </tr>
  {/each}
</tbody>
