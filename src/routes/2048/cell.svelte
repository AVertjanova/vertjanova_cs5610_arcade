<script>
  let { value, row, column } = $props();
</script>

<div class="cell">{value}</div>

<style>
  .cell {
    height: 100px;
    width: 100px;
    border: 1px, solid, grey;
  }
</style>
