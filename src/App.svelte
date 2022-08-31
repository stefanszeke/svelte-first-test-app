<script>
import Counter from "./lib/Counter.svelte";
import FruitsList from "./lib/FruitsList.svelte";
import Title from "./lib/Title.svelte";

</script>

<div class="container">

  <h2>Svelte First Test App</h2>

  <div class='box'> <Title /> <p class='component'>Title.svelte</p></div>

  <div class='box'> <Counter /> <p class='component'>Counter.svelte</p></div>

  <div class='box'> <FruitsList /> <p class='component'>FruitsList.svelte</p></div>

</div>



<style>
  .component {
    position: absolute;
    top: 5px;
    left: 5px;
    color: rgb(177, 177, 177);
    user-select: none;
  }

  h2 {
    text-align: center;
    margin-bottom: 20px;
  }

</style>
