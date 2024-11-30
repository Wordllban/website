<script lang="ts">
	import { i18n } from '$lib/i18n';
	import { ParaglideJS } from '@inlang/paraglide-sveltekit';
	import '../app.css';
	import Header from './Header.svelte';

	let { children } = $props();
</script>

<ParaglideJS {i18n}>
	<div class="px-8">
		<Header />
		{@render children()}
	</div>
</ParaglideJS>
