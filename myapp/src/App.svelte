<script>
  import Info from "./info.svelte";
  import Nested from "./Nested.svelte";

  let name = "hoppe";
  let src = "/tutorial/image.gif";
  let string = `this string contains some <strong>HTML!!!</strong>`;

  let count = 0;

  function incrementCount() {
    count += 1;
  }

  $: doubled = count * 2;
  let hoppe = count * 2;

  $: console.log("the count is " + count);
  $: {
    console.log("the count is " + count);
    alert("I SAID THE COUNT IS " + count);
  }
  $: if (count >= 10) {
    alert("count is dangerously high!");
    count = 9;
  }

  const pkg = {
    name: "svelte",
    version: 3,
    speed: "blazing",
    website: "https://svelte.dev",
  };
</script>

<h1>Hello {name.toUpperCase()}!</h1>
<img {src} alt="{name} dances." />
<p>This is a paragraph.</p>
<Nested answer={42} />
<Nested />
<p>{string}</p>
<p>{@html string}</p>
<button on:click={incrementCount}>
  Clicked {count}
  {count === 1 ? "time" : "times"}
</button>
<p>{count} doubled is {doubled} or {hoppe} ?</p>
<Info {...pkg} />

<style>
  p {
    color: purple;
    font-family: "Comic Sans MS", cursive;
    font-size: 2em;
  }
</style>
