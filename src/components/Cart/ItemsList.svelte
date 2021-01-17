<script>
  import Item from "./Item.svelte";
  import cart, { cartTotal, setStorageCart } from "../../stores/cart";
  import { fly } from "svelte/transition";
  import { flip } from "svelte/animate";
  import {afterUpdate} from 'svelte';
  afterUpdate(() => {
      setStorageCart($cart);
  })

  export let taxes = 0.2;
</script>

<section class="cart-items">
  <article>
    {#each $cart as cartItem, index (cartItem.id)}
      <div
        in:fly={{ delay: (index + 1) * 500, x: 100 }}
        out:fly={{ x: -100 }}
        animate:flip>
        <Item {...cartItem} />
      </div>
    {:else}
      <h2 class="empty-cart">je momentálne prázdny 😢</h2>
    {/each}
  </article>
  <h5>Daň: {taxes * 100}% DPH</h5>
  <h4>Celkom bez DPH: {$cartTotal.toFixed(2)}€</h4>
  <h4>DPH: {($cartTotal * taxes).toFixed(2)}€</h4>
  <h2 class="cart-total">Celkom s DPH: {($cartTotal + $cartTotal * taxes).toFixed(2)}€</h2>
</section>
