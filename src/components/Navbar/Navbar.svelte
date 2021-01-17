<script>
  import BigNavbar from "./BigNavbar.svelte";
  import SmalNavbar from "./SmalNavbar.svelte";
  import globalStore from "../../stores/globalStore";

  let screenWidth;
  $: if (screenWidth > 992) {
      globalStore.toggleItem('sidebar', false);
  }

</script>

<svelte:window bind:innerWidth={screenWidth} />

{#if screenWidth > 992}
  <BigNavbar />
{:else}
  <SmalNavbar />
{/if}
