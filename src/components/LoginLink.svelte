<script>
    import user from '../stores/user';
    import {link} from 'svelte-routing';
    // logout func
    import globalStore from '../stores/globalStore';
</script>


{#if $user.jwt}
<a href="/" class="logout-btn" on:click="{() => {
    globalStore.toggleItem('sidebar', false)
}}">Odhlásiť</a>
{:else}    
<a href="/login" class="logout-btn" on:click="{() => {
    globalStore.toggleItem('sidebar', false)
}}">Prihlásiť</a>
{/if}
