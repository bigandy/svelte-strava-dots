<script lang="ts">
  import Calendar from "$components/Calendar.svelte";
</script>

<div class="App">
  <header class="Header">
    <h1>Svelte Calendar Dots</h1>
  </header>

  <h2>Regular Calendar with no data</h2>
  <Calendar />
</div>

<style>
  .App {
    text-align: center;
    padding: 3rem;
    color: white;
  }

  .Header {
    font-size: calc(10px + 2vmin);
  }
</style>
