<script>
  import { dispatch } from '../store'
  import CityCard from '../components/CityCard.svelte'
  import { router } from 'tinro'

  let cities = ['Charleston, SC', 'New York, NY','San Francisco, CA']

  function changeCurrentCity(city) {
    return async () => {
        await dispatch({type: 'SET_CURRENT', payload: city})
        router.goto('/')
    }
  }
</script>
<nav>
  <div>Favorites</div>
  <a href="">Add</a>
</nav>
<main>
  <section>
    {#each cities as city}
    <CityCard {city} on:click={changeCurrentCity(city)} />
    {/each}
  </section>
</main>
<style>
 nav {
   height: 24px;
   margin-bottom: 0;
   margin-left: 8px;
   margin-right: 8px;
 }
</style>
