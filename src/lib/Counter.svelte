<script>

  let state = 0
  $: reactiveValue = state * 2
  let nonreactiveValue = state * 2

function increment() {
  state++
}

function decrement() {
  if(state > 0) {
    state--
  }
}

function counter(action) {
  if(action === 'increment') state++
  else if(action === 'decrement' && state > 0) state--
}

</script>



<div class='counter'>
  <div class='values'>
    <h1>{state}</h1>
    <h1>{reactiveValue}</h1>
    <h1>{nonreactiveValue}</h1>
  </div>

  <div class="buttons">
      <button on:click={() => counter('increment')}>Increment</button>
      <button on:click={() => counter('decrement')}>Decrement</button>
      
      <button on:click={increment}>+</button>
      <button on:click={decrement}>-</button>
  </div>

</div>



<style>
.counter {
  display: grid;
  font-size: 1.5rem;
  justify-items: center;
}

.values {
  display: grid;
  grid-auto-flow: column;
  justify-content: center;
  grid-gap: 3rem;

  background-color: white;
  border: 1px solid rgb(210, 210, 210);
  border-radius: 6px;
  width: 100%;
  margin: 5px;
}

.counter button {
  width: 80px;
  height: 30px;
  border: none;
  border-radius: 4px;
  background-color: #64a580;
  color: #fff;
  font-weight: bold;
  cursor: pointer;
  transition: 80ms;
}

.counter button:hover {
  background-color: #4c8a6a;
}

.buttons {
  display: grid;
  justify-content: center;
  grid-auto-flow: column;
  gap: 5px;
}

@media screen and (max-width: 500px) {
  .buttons {
    grid-auto-flow: row;
    grid-template-columns: 1fr 1fr;
  }
}

</style>
