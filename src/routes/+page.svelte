<script>
  import BottomSide from "../components/feature/main/cardSides/BottomSide.svelte";
  import FlipCard from "../components/feature/main/FlipCard.svelte";
  import TopSide from "../components/feature/main/cardSides/TopSide.svelte";
</script>

<div class="container">
  <FlipCard>
    <TopSide slot="topSide" />
    <BottomSide slot="bottomSide" />
  </FlipCard>
</div>

<style>
  .container {
    height: 100%;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 32px;
  }
</style>
