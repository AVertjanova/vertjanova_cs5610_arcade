<script>
  let { value, row, column } = $props();
</script>

{#if value === 0}
  <div class="cellBase">{value}</div>
{:else if value === 2}
  <div class="cellBase two">{value}</div>
{:else if value === 4}
  <div class="cellBase four">{value}</div>
{:else if value === 8}
  <div class="cellBase eight">{value}</div>
{:else if value === 16}
  <div class="cellBase sixteen">{value}</div>
{:else if value === 32}
  <div class="cellBase thirtyTwo">{value}</div>
{:else if value === 64}
  <div class="cellBase sixtyFour">{value}</div>
{:else if value === 128}
  <div class="cellBase oneTwentyEight">{value}</div>
{:else if value === 256}
  <div class="cellBase twoFiftySix">{value}</div>
{:else if value === 512}
  <div class="cellBase fiveTwelve">{value}</div>
{:else if value === 1024}
  <div class="cellBase tenTwentyFour">{value}</div>
{:else if value === 2048}
  <div class="cellBase twentyFourtyEight">{value}</div>
{/if}

<style>
  .cellBase {
    height: 100px;
    width: 100px;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: x-large;
    color: #4b3619;
    border: 1px solid #856538;
    margin: 5px;
    background-color: #4b3619;
    border-radius: 15px;
  }
  .two {
    background-color: #fbf4e1;
  }
  .four {
    background-color: #f8e3ac;
  }
  .eight {
    background-color: #f5d176;
  }
  .sixteen {
    background-color: #f3c96f;
  }
  .thirtyTwo {
    background-color: #f1c066;
  }
  .sixtyFour {
    background-color: #efb75d;
  }
  .oneTwentyEight {
    background-color: #ecae54;
  }
  .twoFiftySix {
    background-color: #e89f46;
  }
  .fiveTwelve {
    background-color: #ec893e;
  }
  .tenTwentyFour {
    background-color: #ef7938;
  }
  .twentyFourtyEight {
    background-color: #f26932;
  }
</style>
