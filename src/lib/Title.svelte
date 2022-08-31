<script>

  let colors = ["hotpink","purple","red", "green", "blue"];
  let colorIndex = 0;
  $: titleColor = colors[colorIndex];
  
  function changeColor() { colorIndex < colors.length - 1 ? colorIndex++ : colorIndex = 0 };
  
</script>

  <h2 on:click={changeColor} style="color: {titleColor}">Hello world</h2>
  <p>(click me)</p>

<style>
  h2 {
    font-size: 2rem;
    cursor: pointer;
    user-select: none;
    transition: 120ms;
  }

  h2:hover {
    filter:brightness(0.6);
    transform: scale(1.05);
  }

  p {
    color: rgb(177, 177, 177);
    user-select: none;
    line-height: 0;
  }
</style>



