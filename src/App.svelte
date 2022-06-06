<script>
  import logo from './assets/svelte.png'
  import Counter from './lib/Counter.svelte'
  import Birthday from './lib/Birthday.svelte';

  let birthdays = [
    {id: 1, name: 'Jesus Christ', date: new Date('December 25, 1001'),},
    {id: 2, name: 'Einstein', date: new Date('March 14, 1879'),},
    {id: 3, name: 'Gandhi', date: new Date('October 2, 1869'),},
  ];

  let newBirthdayName = '';
  let newBirthdayDate = null;

  const sortBirthdays = (birthdays, key) => {
    console.info(`Sorted birthdays by ${key}`);
    return;
  }

  function createBirthday() {
    newBirthdayName = newBirthdayName.trim();
    let birthday = {
      id: Math.random(),
      name: newBirthdayName,
      date: newBirthdayDate,
    }
    birthdays = [...birthdays, birthday];
    console.info(`New birthday added:`, birthday);
    newBirthdayName = '';
    newBirthdayDate = null;
    return;
  }

  function deleteBirthday(id) {
    return;
  }

  function exportBirthdays() {
    console.info('Exported birthdays to calendar (.iso)');
    return;
  }
</script>

<main>
  <!-- BRAPP Logo -->
  <img src={logo} alt="Birthday Reminder App Logo" />
  <h1 class="app-title">BRAPP: Birthday reminder app</h1>

  <!-- Add birthday form -->
  <div class="add-birthday-form">
    <form action="" on:submit|preventDefault={createBirthday}>
      <p>Name</p>
      <input class="add-birthday-name" type="text" placeholder="Enter name" bind:value={newBirthdayName} required>
      <p>Date</p>
      <input class="add-birthday-date" type="date" bind:value={newBirthdayDate} required>
      <button class="btn add-birthday-btn">Add birthday</button>
    </form>
 
  </div>

  <Counter />

  <!-- Display list of birthdays, sorted by upcoming date -->
  <div class="container">
    <button on:click={exportBirthdays}>Export Birthdays to Calendar</button>
    <ul class="birthday-list">
      {#each birthdays as birthday (birthday.id)}
        <li>
          <Birthday {...birthday} />
        </li>
      {/each}
    </ul>
  </div>
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
