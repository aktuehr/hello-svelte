<script>
  import Nested from "./Nested.svelte";

  let name = "hoppe";
  let src = "/tutorial/image.gif";
  let string = `this string contains some <strong>HTML!!!</strong>`;

  let count = 0;

  function incrementCount() {
    count += 1;
  }
</script>

<h1>Hello {name.toUpperCase()}!</h1>
<img {src} alt="{name} dances." />
<p>This is a paragraph.</p>
<Nested />
<p>{string}</p>
<p>{@html string}</p>
<button on:click={incrementCount}>
  Clicked {count}
  {count === 1 ? "time" : "times"}
</button>

<style>
  p {
    color: purple;
    font-family: "Comic Sans MS", cursive;
    font-size: 2em;
  }
</style>
