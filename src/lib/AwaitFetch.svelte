<script>

let promise = getRandomCharacter()

function randonNumber() {
  return Math.floor(Math.random() * 20)
}

async function getRandomCharacter() {
  const res = await fetch(`https://swapi.dev/api/people/${randonNumber()}`);
  const character = await res.json();

  if(!res.ok) {throw new Error('something wrong, try again')}
  return character;
}

</script>


<!--  main   -->

{#await promise}
  <p>loading...</p>
{:then character}
  <p>{character.name}</p>
{:catch error}
  <p>{error}</p>
{/await}

<button on:click={() => promise = getRandomCharacter()}>get character from SW api</button>
  
<!--         -->


<style>
  button {
    background-color: rgb(14, 14, 14);
    color: rgb(255, 208, 0);
    border: none;
    padding: 4px 10px;
    border-radius: 4px;
    cursor: pointer;
    transition: 100ms;
  }

  button:hover {
    transform: scale(1.03);
    background-color: rgb(35, 35, 35);
    color: rgb(255, 123, 0);
  }

</style>