<script>
  import logo from './assets/svelte.png'
  import Counter from './lib/Counter.svelte'
  import Birthday from './lib/Birthday.svelte';

  let birthdays =[
    {id: 1, name: 'Jesus Christ', date: new Date('December 25, 1001'),},
    {id: 2, name: 'Einstein', date: new Date('March 14, 1879'),},
    {id: 3, name: 'Gandhi', date: new Date('October 2, 1869'),},
  ];

  function updateBirthdays() {

    console.info('New birthday added!');
  }
</script>

<main>
  <img src={logo} alt="Svelte Logo" />
  <h1>Hello world!</h1>
  <p>BRAPP: Birthday reminder app</p>

  <!-- Birthday creation form -->
  <div class="new-birthday">
    <p>Name</p>
    <input class="new-name" type="text" placeholder="Enter name">
    <p>Date</p>
    <input class="new-date" type="date">
    <button on:click={updateBirthdays}>Add birthday</button>
  </div>

  <Counter />
  {#each birthdays as birthday (birthday.id)}
    <Birthday {...birthday} />
  {/each}
</main>

<style>
  :root {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
      Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  }

  main {
    text-align: center;
    padding: 1em;
    margin: 0 auto;
  }

  img {
    height: 16rem;
    width: 16rem;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4rem;
    font-weight: 100;
    line-height: 1.1;
    margin: 2rem auto;
    max-width: 14rem;
  }

  p {
    max-width: 14rem;
    margin: 1rem auto;
    line-height: 1.35;
  }

  @media (min-width: 480px) {
    h1 {
      max-width: none;
    }

    p {
      max-width: none;
    }
  }
</style>
