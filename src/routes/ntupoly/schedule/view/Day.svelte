
<style>
  .container {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      width: 98%;
      background-color: #fab2b2;
      border-radius: 1rem;
      padding: 2%;
      margin-bottom: 1rem;
  }

  .weekday {
      font-weight: bold;
      text-align: center;
  }
</style>

<script>
  import Slot from './Slot.svelte'

  export let displayOdd
  export let dayIndex
  export let day

  let backgroundColor = "#fab2b2"
  let marginBottom = "1rem"

  if (day.length == 0) {
    backgroundColor = "rgba(0, 0, 0, 0)"
    marginBottom = "0"
  }
  
  function weekday(n) {
    switch (n) {
      case 1:
        return 'Понеділок'
      case 2:
        return 'Вівторок'
      case 3:
        return 'Середа'
      case 4:
        return 'Четвер'
      case 5:
        return "П'ятниця"
      case 6:
        return 'Субота'
      case 7:
        return 'Неділя'
      default:
        return 'Unknown'
    }
  }
</script>

<div style:background-color={backgroundColor} class="container">
  <span style:margin-bottom={marginBottom} class="weekday">{weekday(dayIndex + 1)}</span>
  {#each day as slot, slotIndex}
      <Slot bind:displayOdd {slotIndex} {slot} />
  {/each}
</div>
