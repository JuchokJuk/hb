<script>
  import Header from "../../../shared/fontSystem/Header.svelte";
</script>

<div class="card">
  <!-- svelte-ignore a11y-missing-attribute -->
  <img src="/images/lesha.png">
  <div class="header">
    <Header>С днём рождения,</Header>
    <Header>Лёша!!11!!!!1</Header>
  </div>
</div>

<style>
  .card {
    display: grid;
    grid-template-columns: 1fr;
    gap: 58px;
    justify-items: center;
    align-content: center;

    width: 100%;
    height: 100%;
    max-width: 506px;
    max-height: 506px;

    padding: 32px;

    background: white;
    border-radius: 8px;
  }

  .header {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  img{
    max-height: 300px;
    border-radius: 4px;
  }
</style>
