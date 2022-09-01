<script>

let fruits = [
  {
    name: 'Apple',
    price: 1,
    image: '../../public/fruitsIMG/apple.png'
  },
  {
    name: 'Orange',
    price: 2,
    image: '../../public/fruitsIMG/orange.png'
  },
  {
    name: 'Banana',
    price: 3,
    image: '../../public/fruitsIMG/banana.png'
  }
]

let fruitCounter = []

function addFruits(index) {
  fruitCounter[index] = fruitCounter[index] + 1 || 1
}

function removeFruits(index) {
  if(fruitCounter[index] > 0) {
    fruitCounter[index]--
  }
}

$: total = fruitCounter.reduce((acc, curr, index) => acc + curr*fruits[index].price, 0)


</script>


<!--  main   -->

<div class="fruits-list">

  <div class='legend'>
    <p>name</p>
    <p>price</p>
    <p>buy</p>
    <p>img</p>

  </div>

  {#each fruits as fruit, index}
    <div class="fruit">

      <div class="name">{fruit.name}</div>
      <div class="price">${fruit.price.toFixed(2)}</div>

      <div class='buy'>
        <button on:click={() => addFruits(index)}>+</button>
        <p>{fruitCounter[index] | 0}</p>
        <button on:click={() => removeFruits(index)}>-</button>
      </div>



      {#if ['A','E','I','O','U','Y'].includes(fruit.name[0])}
      <div class="image" ><img src={fruit.image} alt='photo of an {fruit.name}'/></div>
      {:else}
      <div class="image" ><img src={fruit.image} alt='photo of a {fruit.name}'/></div>
      {/if}
    </div>
  {/each}
  <h3 class="total">Total: {total.toFixed(2)} $</h3>


</div>

<!--         -->


<style>

  .fruits-list {
    display: grid;
    gap: 0.5rem;
    margin-top: 10px;
    width: 100%;
  }
  
  .fruit {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr;
    align-items: center;

    width: 100%;
  
    justify-items: center;

    border: 2px solid rgb(100, 130, 100);
    background-color: rgb(246, 246, 245);
    border-radius: 10px;

    font-size: 1.5rem;
  }

  .fruit img {
    width: 60px;
    height: 60px;
  }

  .buy {
    width: 80%;
    height: 50%;
    display: grid;
    grid-template-columns: 20% 1fr 20%;
    align-items: center;
    gap: 0.5rem;
    background: rgb(73, 101, 139);

    color: white;

    border-radius: 5px;
    overflow: hidden;
  }

  .buy button {
    height: 100%;
    border: none;
    background-color: rgb(181, 188, 214);
    font-size: 1.5rem;
    cursor: pointer;
  }

  .buy button:hover {
    background-color: rgb(147, 153, 174);
    color: white;
  }

  .buy p {
    user-select: none;
    text-align: right;
  }

  .legend {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr;
    align-items: center;
  }

  .legend p {
    display: grid;
    justify-items: center;
  }

  .total {
    text-align: right;
  }


</style>