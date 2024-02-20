<script lang="ts">
  import { indexToDay } from "./utils";

  const { rowIndex, columnIndex, firstDayofMonth, daysInMonth, todayDay } =
    $props<{
      rowIndex: number;
      columnIndex: number;
      firstDayofMonth: number;
      daysInMonth: number;
      todayDay: number;
    }>();

  const dayNumber = $derived(
    rowIndex * 7 + 1 * (columnIndex + 1) - firstDayofMonth + 1
  );

  const isCalendarDay = $derived(dayNumber < daysInMonth + 1 && dayNumber > 0);
  const isToday = $derived(dayNumber > 0 && dayNumber === todayDay);

  const dayName = indexToDay(columnIndex + 1);
</script>

<td>
  {isCalendarDay ? `${dayName} - ${dayNumber}` : ""}<br />
  {isToday ? "today" : ""}
  <span class="dayName vh">
    {dayName}
  </span>
  <span>
    {isCalendarDay ? dayNumber : ""}
  </span>
</td>
