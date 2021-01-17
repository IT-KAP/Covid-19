<script>
  // pages
  import Login from "./pages/Login.svelte";
  import Checkout from "./pages/Checkout.svelte";
  import ProductTemplate from "./pages/ProductTemplate.svelte";
  import Products from "./pages/Products.svelte";
  import Home from "./pages/Home.svelte";
  import About from "./pages/About.svelte";

  // router
  import { Router, Route } from "svelte-routing";
  import Navbar from "./components/Navbar/Navbar.svelte";
  import Sidebar from "./components/Navbar/Sidebar.svelte";
  import Cart from "./components/Cart/Cart.svelte";
  // global store
  import globalStore from "./stores/globalStore";
</script>

<style>
</style>

<Router>
  <Navbar />
  {#if $globalStore.sidebar}
    <Sidebar />
  {/if}
  {#if $globalStore.cart}
    <Cart />
  {/if}
  <Route path="/">
    <Home />
  </Route>
  <Route path="o-nas" component={About} />
  <Route path="login" component={Login} />
  <Route path="produkty" component={Products} />
  <Route path="produkty/:id" component={ProductTemplate} />
</Router>
