<script>
  import Hero from "../components/Hero.svelte";
  import { link } from "svelte-routing";
  import Featured from "../components/Products/Featured.svelte";

  // featured products
</script>


<Hero>
  <a href="/produkty" class="btn btn-primary btn-hero" use:link>Nakupovať</a>
</Hero>
<Featured title="Vybrané produkty" />
