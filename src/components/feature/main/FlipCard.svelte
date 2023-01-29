<script>
    import { onMount } from "svelte";
  import DancingCats from "./confetti/DancingCats.svelte";
  import Emojis from "./confetti/Emojis.svelte";

  let flipped = false;

  function flip() {
    flipped = !flipped;
  }

  let audio;

  onMount(()=>{
    audio = new Audio('/music/sax.mp3');
    audio.loop = true;
  })

  $:{
    if(flipped){
      audio.play();
    }else{
      if(audio){
        audio.pause();
      }
    }
  }
</script>

{#if flipped}
  <DancingCats />
{/if}

<!-- svelte-ignore a11y-click-events-have-key-events -->
<div class="flip-card" on:click={flip} class:flipped>
  <div class="flip-card-inner">
    <div class="flip-card-front">
      <slot name="topSide" />
    </div>
    <div class="flip-card-back">
      <slot name="bottomSide" />
    </div>
  </div>
</div>

{#if flipped}
  <Emojis />
{/if}

<style>
  .flip-card {
    width: 506px;
    height: 506px;
    perspective: 1000px;
    cursor: pointer;
  }

  .flip-card-inner {
    position: relative;
    width: 100%;
    height: 100%;
    transition: transform 0.8s;
    transform-style: preserve-3d;
  }

  .flip-card.flipped .flip-card-inner {
    transform: rotateY(180deg);
  }

  .flip-card-front,
  .flip-card-back {
    position: absolute;
    width: 100%;
    height: 100%;
    -webkit-backface-visibility: hidden;
    backface-visibility: hidden;
  }

  .flip-card-back {
    transform: rotateY(180deg);
  }
</style>
