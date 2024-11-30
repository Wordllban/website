<script lang="ts">
	import { Menu, MoonStar, X as XIcon } from 'lucide-svelte';
	import { Button } from '$lib/components/ui/button';
	import { cn } from '$lib/utils';
	import { Popover, PopoverContent, PopoverTrigger } from '$lib/components/ui/popover';

	let showMobile = $state(false);

	function handleShowMobile() {
		showMobile = !showMobile;
	}
</script>

<nav class="flex flex-col items-end text-2xl">
	<div class="hidden gap-6 p-4 md:flex md:pr-40">
		<a
			href="/skills"
			class="flex items-center gap-2 rounded-md px-2 py-2 opacity-80 hover:opacity-100">Skills</a
		>
		<a
			href="/projects"
			class="flex items-center gap-2 rounded-md px-2 py-2 opacity-80 hover:opacity-100">Projects</a
		>
		<a
			href="/resume"
			class="flex items-center gap-2 rounded-md px-2 py-2 opacity-80 hover:opacity-100">Resume</a
		>
		<Popover>
			<PopoverTrigger
				class="flex items-center justify-center rounded-md px-2 py-2 opacity-80 hover:opacity-100"
			>
				Links
			</PopoverTrigger>
			<PopoverContent class="mt-1.5 w-fit rounded-md p-1">
				<span class={cn('flex flex-col gap-1 px-4 py-2')}>
					<span>linkedin</span>
					<span>github</span>
					<span>steam</span>
				</span>
			</PopoverContent>
		</Popover>
	</div>

	<span class={cn('p-4 md:hidden', showMobile ? 'invisible' : 'inline')}>
		<Button variant="icon" size="icon" onclick={handleShowMobile}>
			<Menu />
		</Button>
	</span>

	<div
		class={cn(
			'fixed top-0 z-50 flex w-full justify-end',
			'transform transition-transform duration-300 ease-in-out',
			showMobile ? 'translate-x-0' : 'translate-x-full'
		)}
		aria-hidden={!showMobile}
	>
		<span class="h-screen w-1/5 bg-background/50 backdrop-blur-[2px]"></span>
		<div class="ml-auto flex h-screen w-4/5 flex-col rounded-l-2xl p-4 backdrop-blur-[2px]">
			<span class="mb-4 flex w-full justify-end">
				<Button
					variant="icon"
					size="icon"
					aria-label="close menu"
					class="h-10 w-10 border border-border"
					onclick={handleShowMobile}
				>
					<XIcon />
				</Button>
			</span>

			<span class="flex flex-col p-1">
				<a href="/skills" class="flex items-center gap-2 rounded-md px-2 py-3.5 hover:bg-accent"
					>Skills</a
				>
				<a href="/projects" class="flex items-center gap-2 rounded-md px-2 py-3.5 hover:bg-accent"
					>Projects</a
				>
				<a href="/resume" class="flex items-center gap-2 rounded-md px-2 py-3.5 hover:bg-accent"
					>Resume</a
				>
			</span>
		</div>
	</div>
</nav>
