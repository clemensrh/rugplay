<script lang="ts">
	import { getPublicUrl } from '$lib/utils';

	let {
		icon,
		symbol,
		name = symbol,
		size = 6,
		class: className = ''
	} = $props<{
		icon?: string | null;
		symbol: string;
		name?: string;
		size?: number;
		class?: string;
	}>();

	let sizeClass = $derived(`h-${size} w-${size}`);
</script>

{#if icon}
	<img
		src={getPublicUrl(icon)}
		alt={name}
		class="{sizeClass} rounded-full object-cover {className}"
		loading="lazy"
		decoding="async"
	/>
{:else}
	<div
		class="{sizeClass} bg-primary flex items-center justify-center overflow-hidden rounded-full {className}"
	>
		<span class="text-xs font-bold text-white">{symbol.slice(0, 2)}</span>
	</div>
{/if}
