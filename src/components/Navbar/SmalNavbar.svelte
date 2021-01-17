<script>
  // cart button
  // global store
  import { link } from "svelte-routing";
  import CartButton from "../Cart/CartButton.svelte";
  import globalStore from "../../stores/globalStore";
  let openSidebar = globalStore.toggleItem
</script>

<style>
  .navbar {
    background: #fff;
  }
</style>

<nav class="navbar">
  <div class="nav-center">
    <!-- sidbar toggle -->
    <button class="btn-sidebar-toggle" on:click={() => {
        openSidebar('sidebar', true);
        }}><i class="fas fa-bars" /></button>
    <!-- logo -->
    <a href="/" use:link class="nav-logo"><img
        src="/assets/images/logo.svg"
        class="logo"
        alt="covid logo" />
    </a>
    <!-- cart button -->
    <CartButton />
  </div>
</nav>
