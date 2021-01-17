<script>
  export let id;
 // export let location;

  import { addToCart } from "../stores/cart";
  import products from "../stores/defaultProducts";
  import { link } from "svelte-routing";
  import Loading from "../components/Products/Loading.svelte";
  import globalStore from "../stores/globalStore";
  $: product = $products.find((item) => item.id === parseInt(id));
</script>

<svelte:head>
  <title>{!product ? 'jeden produkt' : product.title}</title>
</svelte:head>
{#if !products}
  <Loading />
{:else}
  <section class="single-product">
    <!-- back to products -->
    <a href="/produkty" use:link class="btn btn-white">späť na produkty</a>
    <!-- single product container -->
    <div class="single-product-container">
      <article class="single-product-image">
        <img src={product.image} alt={product.title} />
      </article>
      <article>
        <h1>{product.title}</h1>
        <h2>{product.price.toFixed(2)}€ bez DPH</h2>
        <p>{product.description}</p>
        <button
          class="btn btn-primary btn-block"
          on:click={() => {
            addToCart(product);
            globalStore.toggleItem('cart', true);
          }}>vložiť do košíka</button>
      </article>
    </div>
  </section>
{/if}

<style>
 .btn-primary:hover {
    background-color: rgb(18, 167, 13);
    color: #fff;
  }
  .btn-white {
    background-color: var(--mainBlack)
  }
  .btn-white:hover {
    background-color: var(--mainWhite);
    color: var(--mainBlack);
  }
</style>