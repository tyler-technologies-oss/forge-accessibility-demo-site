<script>
	import { onMount } from 'svelte';
	import { createEventDispatcher } from 'svelte';

	async function loadForgeComponents() {
		import('@tylertech/forge/esm/list');
	}

	onMount(async () => {
		await loadForgeComponents();
	});

	const dispatch = createEventDispatcher();
	const dispatchNavItemClicked = () => {
		dispatch('nav-item-clicked');
	};

	let navItems = [
		{
			label: 'Dashboard',
			value: 'dashboard',
			href: '/',
			icon: 'dashboard'
		},
		{
			label: 'Settings',
			value: 'settings',
			href: '/settings',
			icon: 'settings'
		}
	];
</script>

<nav>
	<forge-list on:forge-list-item-select={dispatchNavItemClicked}>
		{#each navItems as navItem, index}
			<forge-list-item id={`nav-item-${navItem.value}`} href={navItem.href}>
				<forge-icon slot="leading" name={navItem.icon} external></forge-icon>
				{navItem.label}
				<forge-tooltip target={`nav-item-${navItem.value}`}>{navItem.label}</forge-tooltip>
			</forge-list-item>
		{/each}
	</forge-list>
</nav>
