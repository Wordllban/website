<script lang="ts">
	import { i18n } from '$lib/i18n';
	import { ParaglideJS } from '@inlang/paraglide-sveltekit';
	import '../app.css';
	import Header from './Header.svelte';

	let { children } = $props();
</script>

<ParaglideJS {i18n}>
	<div>
		<Header />
		<div class="px-8 md:px-32">
			{@render children()}
		</div>
	</div>
</ParaglideJS>
