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

  let user = { loggedIn: false };

  function toggle() {
    user.loggedIn = !user.loggedIn;
  }

  let x = 7;
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

{#if user.loggedIn}
  <button on:click={toggle}>Log out</button>
{:else}
  <button on:click={toggle}>Log in</button>
{/if}

{#if x > 10}
  <p>{x} is grater than 10</p>
{:else if 5 > x}
  <p>{x} is less than 5</p>
{:else}
  <p>{x} is between 5 and 10</p>
{/if}

<style>
  p {
    color: purple;
    font-family: "Comic Sans MS", cursive;
    font-size: 2em;
  }
</style>
