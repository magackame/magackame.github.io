
<style>
  .container {
      display: flex;
      justify-content: center;
      align-items: center;
      width: 100%;
      margin-bottom: 1rem;
  }

  .roman {
      font-weight: bold;
      font-size: x-large;
      text-align: center;
      width: 5rem;
  }  
</style>

<script>
  import Lesson from './Lesson.svelte'

  export let displayOdd
  export let slotIndex
  export let slot

  function roman(n) {
    switch (n) {
      case 1:
        return 'I'
      case 2:
        return 'II'
      case 3:
        return 'III'
      case 4:
        return 'IV'
      case 5:
        return 'V'
      case 6:
        return 'VI'
      case 7:
        return 'VII'
      case 8:
        return 'VIII'
      case 9:
        return 'IX'
      case 10:
        return 'X'
      default:
        return n
    }
  }

  $: displaySwitchButton = slot.odd || slot.even

  let lesson = slot.whole

  $: if (!slot.whole) {
    if (displayOdd) {
      lesson = slot.odd
    } else {
      lesson = slot.even
    }
  }

</script>

<div class="container">
  <span class="roman">{roman(slotIndex + 1)}</span>

  <Lesson bind:displayOdd {displaySwitchButton} {lesson} />
</div>