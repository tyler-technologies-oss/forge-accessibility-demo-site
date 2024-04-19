<script>
	import { onMount } from 'svelte';
	import { createEventDispatcher } from 'svelte';

	onMount(async () => {
		import('@tylertech/forge/esm/list');
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
			iconLibrary: 'standard',
			icon: 'dashboard'
		},
		{
			label: 'Forms',
			value: 'forms',
			href: '/forms',
			iconLibrary: 'extended',
			icon: 'file_document_edit'
		},
		{
			label: 'Settings',
			value: 'settings',
			href: '/settings',
			iconLibrary: 'standard',
			icon: 'settings'
		}
	];
</script>

<nav>
	<forge-list on:forge-list-item-select={dispatchNavItemClicked}>
		{#each navItems as navItem, index}
			<forge-list-item
				id={`nav-item-${navItem.value}`}
				href={navItem.href}
				data-arc={`nav-${navItem.value}`}
			>
				<forge-icon slot="leading" name={navItem.icon} external external-type={navItem.iconLibrary}
				></forge-icon>
				{navItem.label}
				<forge-tooltip target={`nav-item-${navItem.value}`}>{navItem.label}</forge-tooltip>
			</forge-list-item>
		{/each}
	</forge-list>
</nav>
