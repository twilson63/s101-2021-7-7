<script>
  import { Route } from 'tinro'

  import Current from './views/Current.svelte'
  import Favorites from './views/Favorites.svelte'
  import Add from './views/Add.svelte'
</script>
<Route path="/">
  <Current />
</Route>
<Route path="/favorites">
  <Favorites />
</Route>
