<script>
	import { walletStore } from '@aztemi/svelte-on-solana-wallet-adapter-core';
</script>

{#if $walletStore?.connected}
	<div>My wallet is connected</div>
{/if}

<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>
