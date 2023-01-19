
<style>
  @import url('https://fonts.googleapis.com/css2?family=Comfortaa:wght@500&display=swap');

  * {
      font-family: 'Comfortaa';
  }

  :global(body) {
      padding: 0;
      margin: 0;
      background-color: #262626;
      font-size: large;
  }

  .main {    
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      width: 90%;
      padding: 5%;
      color: #757575;
  }

  .container {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      width: 100%;
      max-width: 40rem;
  }

  .message {
    font-size: x-large;
    text-align: center;
    color: #fab2b2;
  }
</style>

<script>
  import Day from './Day.svelte'
  import schedule from './schedule.json'

  let displayOdd = true
</script>

<div class="main">
  <div class="container">
    {#each schedule.days as day, dayIndex}
      <Day bind:displayOdd {dayIndex} {day} />
    {/each}
  </div>
</div>