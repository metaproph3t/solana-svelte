<script lang="ts">
	import { onMount } from 'svelte';
	import { PhantomWalletAdapter, SolflareWalletAdapter } from '@solana/wallet-adapter-wallets';
	import { WalletProvider, WalletMultiButton } from '@aztemi/svelte-on-solana-wallet-adapter-ui';
	import type { Adapter } from '@solana/wallet-adapter-base';

	const logoPath = '/logo.png';
	let wallets: Adapter[];

	onMount(() => {
		wallets = [new PhantomWalletAdapter(), new SolflareWalletAdapter()];
	});
</script>

<main class="app-container">
	<header class="app-header">
		<div class="logo-container">
			<img src={logoPath} alt="Decision Market Platform Logo" />
			<h1>Decision Markets</h1>
		</div>
		<nav class="main-nav">
			<a href="#home">Home</a>
			<a href="#positions">Positions</a>
			<a href="#analytics">Analytics</a>
		</nav>
		<div class="wallet-container">
			<WalletProvider localStorageKey="walletAdapter" {wallets} autoConnect />
			<WalletMultiButton />
		</div>
	</header>

    <section class="main-content">
        <slot />
    </section>
</main>

<style>
	:global(body) {
		margin: 0;
		font-family: 'Roboto', sans-serif;
		background-color: #0a0a0a;
		color: #e0e0e0;
	}

	.app-container {
		display: flex;
		flex-direction: column;
		height: 100vh;
	}

	.app-header {
		background-color: #111;
		border-bottom: 1px solid #fc494a;
		padding: 0.5rem 1rem;
		display: flex;
		justify-content: space-between;
		align-items: center;
	}

	.logo-container {
		display: flex;
		align-items: center;
	}

	.logo-container img {
		height: 30px;
		margin-right: 0.5rem;
	}

	.logo-container h1 {
		font-size: 1.2rem;
		color: #fc494a;
		margin: 0;
	}

	.main-nav {
		display: flex;
		gap: 1rem;
	}

	.main-nav a {
		color: #fff;
		text-decoration: none;
		font-size: 0.9rem;
		transition: color 0.3s ease;
	}

	.main-nav a:hover {
		color: #fc494a;
	}

	.wallet-container {
		display: flex;
		align-items: center;
	}

	.content-area {
		display: flex;
		flex: 1;
		overflow: hidden;
	}

	.main-content {
		flex: 1;
		padding: 1rem;
		overflow-y: auto;
	}
</style>
