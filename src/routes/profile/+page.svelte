<script>
  import { Datepicker } from 'flowbite-svelte';
</script>

<style>
  :global(html, body) {
      margin: 0;
      padding: 0;
      height: 100%; /* Ensure the body takes the full height of the viewport */
      
  }

  .dashboard {
      display: grid;
      grid-template-areas:
          "summary calendar"
          "booking calendar";
      grid-template-columns: 2fr 2fr;
      grid-template-rows: auto 1fr;
      gap: 1rem;
      height: 100vh;
      padding: 1rem;
      justify-content: center;
      background-color: #DBDBDB;
  }

  .box {
      background-color: #ECEBEB;
      border-radius: 0.5rem;
      padding: 1rem;
  }

  .summary {
      grid-area: summary;
      padding: 2rem;
  }

  .booking {
      grid-area: booking;
      padding: 2rem;
  }

  .calendar {
      grid-area: calendar;
      padding: 2rem;
  }
</style>

<div class="dashboard">
  <div class="box summary"></div>
  <div class="box booking"></div>
  <div class="box calendar"></div>
</div>
