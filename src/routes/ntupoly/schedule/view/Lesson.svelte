
<style>
  .container {
      display: flex;
      flex-direction: column;
      justify-content: center;
      background-color: #fad0d0;
      border-radius: 1rem;
      width: 100%;
      min-height: 4rem;
      padding: 0.75rem;

      transition: all 0.6s ease-out;
  }

  .subject {
      font-weight: bold;
      margin-bottom: 0.5rem;
  }

  .teacher {
      font-size: medium;
  }

  .switch {
      text-align: center;
      width: 6rem;
      border-radius: 0.5rem;
      border-width: 0px;
      padding: 0.25rem;
      color: white;
      background-color: blue;
  }
</style>

<script>
  import { fade } from 'svelte/transition'

  export let displayOdd
  export let displaySwitchButton
  export let lesson


  let backgroundColor = undefined
  $: if (!lesson) {
    backgroundColor = "rgba(0, 0, 0, 0)"
  } else {
    backgroundColor = "#fad0d0"
  }

  let marginBottom = undefined
  if (displaySwitchButton) {
    marginBottom = "0.5rem"
  } else {
    marginBottom = "0"
  }

  let switchButtonText = undefined
  $: if (displayOdd) {
    switchButtonText = 'Чисельник'
  } else {
    switchButtonText = 'Знаменник'
  }

  function switchButtonClicked() {
    displayOdd = !displayOdd
  }
</script>

<div style:background-color={backgroundColor} class="container">
  {#if lesson}
    <span class="subject">{lesson.subject}</span>
    <span style:margin-bottom={marginBottom} class="teacher">{lesson.teacher}</span>
  {/if}
  {#if displaySwitchButton}
    <button on:click={switchButtonClicked} class="switch">
      {switchButtonText}
    </button>
  {/if}
</div>
