<script>
  import { fade } from "svelte/transition";
  import { onMount } from "svelte";
  import { shuffle } from "../../../../helpers/shuffle";

  const partyEmojis = ["🥳", "🎉", "✨"];

  const singingEmojis = [
    "🎷🦍",
    "🎷🐩",
    "🎷🐈",
    "🎷🐈‍⬛",
    "🎷🐅",
    "🎷🐆",
    "🎷🦄",
    "🎷🐖",
    "🎷🐗",
    "🎷🐑",
    "🎷🐘",
    "🎷🦛",
    "🎷🐇",
    "🎷🐿️",
    "🎷🦔",
    "🎷🦥",
    "🎷🐤",
    "🎷🦜",
    "🎷🐢",
    "🎷🦕",
    "🎷🐋",
    "🎷🦭",
    "🎷🐠",
    "🎷🐌",
    "🎷🐛",
    "🎷🐝",
  ];

  let emojis = [];
  for (let i = 0; i < 32; i++) {
    emojis = [...emojis, ...partyEmojis];
  }
  emojis = [...emojis, ...singingEmojis];

  shuffle(emojis);

  let confetti = new Array(64)
    .fill()
    .map((_, i) => {
      return {
        character: emojis[i % emojis.length],
        x: Math.random() * 100,
        y: -20 - Math.random() * 100,
        r: 0.1 + Math.random() * 1,
      };
    })
    .sort((a, b) => a.r - b.r);

  onMount(() => {
    let frame;

    function loop() {
      frame = requestAnimationFrame(loop);

      confetti = confetti.map((emoji) => {
        emoji.y += 0.7 * emoji.r;
        if (emoji.y > 120) emoji.y = -20;
        return emoji;
      });
    }

    loop();

    return () => cancelAnimationFrame(frame);
  });
</script>

<div class="container" out:fade={{ duration: 400 }}>
  {#each confetti as c}
    <span class="emoji" style="left: {c.x}%; top: {c.y}%; transform: scale({c.r})">{c.character}</span>
  {/each}
</div>

<style>
  .container {
    position: fixed;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    width: 100%;
    height: 100%;
    overflow: hidden;
    pointer-events: none;
  }

  .emoji {
    position: absolute;
    font-size: 64px;
  }
</style>
