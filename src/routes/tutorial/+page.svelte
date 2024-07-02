<h1>tutorial</h1>
<p>this is the tutorial page.</p>


<script>
  let name = 'Vladimir';
  // let src = '/home/pleshco@work.deeplace.md/www/myfirstsvelte/src/routes/tutorial/burg.png';
  import src from './parrot.gif';
  import Nested from './Nested.svelte';
  import Info from './Info.svelte';
  let alt = 'A magician on the hill.';
  let count = 0;
  $: doubled = count * 2;
  $: {
    // console.log('the count is ' + count);
	  // alert('I SAID THE COUNT IS ' + count);
    if (count >= 10) {
      alert('count is dangerously high!');
      count = 9;
    }
  }
  function incrementCount() {
    count += 1;
  }

  let numbers = [1, 2, 3, 4];

  function addNumber() {
    // numbers.push(numbers.length + 1);
    // numbers = numbers;

    // numbers = [...numbers, numbers.length + 1];

    numbers[numbers.length] = numbers.length + 1;
  }

  $: sum = numbers.reduce((t, n) => t + n, 0);

  const pkg = {
    name: 'svelte',
    version: 3,
    speed: 'blazing',
    website: 'https://svelte.dev'
  };

  let user = { loggedIn: false };

  function toggle() {
    user.loggedIn = !user.loggedIn;
  }

  let x = 7;

  let cats = [
    { id: 'J---aiyznGQ', name: 'keyboard Cat' },
    { id: 'z_AbfPXTKms', name: 'Maru' },
    { id: 'OUtn3pvWmpg', name: 'Henri The Existential Cat' }
  ];

  import Thing from './Thing.svelte';

  let things = [
    {id: 1, name: 'apple'},
    {id: 2, name: 'banana'},
    {id: 3, name: 'carrot'},
    {id: 4, name: 'doughnut'},
    {id: 5, name: 'egg'},
  ];

  function handleClick() {
    things = things.slice(1);
  }

</script>

<h2>Hello {name.toUpperCase()}!</h2>
<img src={src} alt={alt} />

<p>This is a paragraph</p>
<Nested answer={42} />

<Nested />

<button on:click={incrementCount}>
  clicked {count}
  {count === 1 ? 'time' : 'times'}
</button>

<p>{count} doubled is {doubled}</p>

<p>{numbers.join(' + ')} = {sum}</p>

<button on:click={addNumber}> Add a number</button>

<Info {...pkg} />

{#if user.loggedIn}
  <button on:click={toggle}>Log out</button>
<!-- {/if} -->
<!-- {#if !user.loggedIn} -->
{:else}
  <button on:click={toggle}>Log in</button>
{/if}

{#if x > 10}
	<p>{x} is greater than 10</p>
{:else if 5 > x}
	<p>{x} is less than 5</p>
{:else}
	<p>{x} is between 5 and 10</p>
{/if}

<h1> The famous Cats of YouTube</h1>
<ul>
  {#each cats as {id, name}}
    <li>
      <a target="_blank" href="https://www.youtube.com/watch?v={id}" rel="noreferrer">
        {id}: {name}
      </a>
    </li>
  {/each}
</ul>

<button on:click={handleClick}> Remove first thing </button>

{#each things as thing (thing.id)}
  <Thing name={thing.name} />
{/each}

<style>
  p {
    color: purple;
    font-family: 'Comic Sans MS', cursive;
    font-size: 2em;
  }

  button {
    width:200px;
  }
</style>

