<script lang="ts">
	import { fade } from 'svelte/transition';

	const links = ['https://tailwindcss.com/', 'https://svelte.dev/', 'https://heroicons.com/'];
	let openLinksInNewTab = true;

	let count = 0;

	let visible = false;
	setTimeout(() => (visible = true), 100);
</script>

{#if visible}
	<div class="p-4 rounded-lg border" transition:fade={{ duration: 500 }}>
		<div class="font-bold text-orange-500 text-xl">Hello world</div>
		<div>
			<div class="font-bold">Reference Links</div>
			<div>
				Open Link in New Tab <input type="checkbox" bind:checked={openLinksInNewTab} />
			</div>
			{#each links as link}
				<div>
					<a
						target={openLinksInNewTab ? '_blank' : null}
						class="text-blue-400 underline"
						href={link}>{link}</a
					>
				</div>
			{/each}
		</div>
		<div class="font-bold">What will you create today?</div>
		<div class="flex items-center">
			Basic counter: <button
				on:click={() => (count = count + 1)}
				class="ml-1 w-32 flex bg-purple-500 p-1 rounded-lg border-purple-300 border"
			>
				<!-- Hero Icons -->
				<svg
					xmlns="http://www.w3.org/2000/svg"
					fill="none"
					viewBox="0 0 24 24"
					stroke-width="1.5"
					stroke="currentColor"
					class="w-6 h-6 text-cyan-200"
				>
					<path
						stroke-linecap="round"
						stroke-linejoin="round"
						d="M15.042 21.672L13.684 16.6m0 0l-2.51 2.225.569-9.47 5.227 7.917-3.286-.672zM12 2.25V4.5m5.834.166l-1.591 1.591M20.25 10.5H18M7.757 14.743l-1.59 1.59M6 10.5H3.75m4.007-4.243l-1.59-1.59"
					/>
				</svg>
				Click me: {count}
			</button>
		</div>
	</div>
{/if}
