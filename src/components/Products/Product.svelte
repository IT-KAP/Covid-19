<script>
    export let product;
    const { title, image, price, id } = product;
    import { link } from 'svelte-routing';

</script>

<article class="product">
    <div class="img-container">
        <img src={image} alt={title} />
        <a href={`/produkty/${id}`} class="btn btn-primary product-link"
        use:link>detail</a>
    </div>
    <div class="product-footer">
    <p class="product-title">{title}</p>
    <p class="product-price">{price.toFixed(2)}€ bez DPH</p>
    </div>
</article>