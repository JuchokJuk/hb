<script>
  import Header from "../../../shared/fontSystem/Header.svelte";
  import Text from "../../../shared/fontSystem/Text.svelte";
</script>

<div class="card">
  <div class="placeholder">
    <Text>нужно фотку вставить сюда</Text>
  </div>
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

    background: hsl(120, 62%, 83%);
    border-radius: 8px;
  }

  .header {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .placeholder {
    background: gray;
    display: flex;
    align-items: center;
    justify-content: center;
    padding-top: 128px;
    padding-bottom: 128px;
    padding-left: 32px;
    padding-right: 32px;
    border-radius: 4px;
  }
</style>
