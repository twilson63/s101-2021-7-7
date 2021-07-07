<script>
  import { getJSON } from '../lib/async.js'
  import { onMount } from 'svelte'

  import { fahrenheitToCelsius, celsiusToFahrenheit } from 'temperature'

  import Weather from '../components/Weather.svelte'
    
  let weather = {
    city: 'Charleston, SC',
    temp: '80 &deg; F',
    icon: 'a01n',
      description: 'clear',
      foo: 'bar'
    
  }
    
  function getWeather() {
    return getJSON('/api/weather?city=charleston,sc&country=us')
    .then(results => ({
          temp: `${results.temp} &deg; C`,
          icon: results.weather.icon,
          description: results.weather.description,
          city: `${results.city_name} ${results.state_code}`
      })
      )
  }

    let temp = 21.7;
    let unit = "c"

    $: displayTemp = `${Math.floor(temp)} &deg; ${unit.toUpperCase()}`
    

  function convertToF() {
    temp = celsiusToFahrenheit(temp)
    unit = "f"
  }
  function convertToC() {
    temp = fahrenheitToCelsius(temp)
    unit = "c"
  }
</script>
<nav>
  <div>
    <a href="" on:click|preventDefault={convertToF}>F</a>
    |
    <a href="" on:click|preventDefault={convertToC}>C</a>
  </div>
  <a href="/favorites">Favorites</a>
</nav>
<main>
  {#await getWeather()}
    Loading...
  {:then weather}
    <Weather {...weather} />
  {/await}
</main>
<style>
  nav {
    margin-bottom: 0;
    margin-left: 8px;
    margin-right: 8px;
  }
  main {
    display: flex;
    flex-direction: column;
    align-items: center;
  }


</style>


