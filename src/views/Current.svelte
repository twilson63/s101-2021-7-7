<script>
  import { fahrenheitToCelsius, celsiusToFahrenheit } from 'temperature'

  import Weather from '../components/Weather.svelte'

    let temp = 21.7;
    let unit = "c"

    $: displayTemp = `${Math.floor(temp)} &deg; ${unit.toUpperCase()}`
    

  const weather = {
    city: 'Charleston, SC',
    temp: '80 &deg; F',
    icon: 'a01n',
      description: 'clear',
      foo: 'bar'
    
  }
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
  <a href="">Favorites</a>
</nav>
<main>
  {@html displayTemp}
  <Weather {...weather} />
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


