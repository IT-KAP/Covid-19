<script>
  export let title = "";
  import products from "../../stores/defaultProducts";
  import Loading from "./Loading.svelte";
  import Product from "./Product.svelte";
</script>

<section class="section">
  <h2 class="section-title">{title}</h2>
  <div class="products-center">
    {#each $products as product (product.id)}
      <Product {product} />
    {:else}
      <Loading />
    {/each}
  </div>
</section>
