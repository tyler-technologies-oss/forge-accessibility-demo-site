<script>
	import IconPickerAutocomplete from '$lib/components/IconPickerAutocomplete.svelte';
	import { onMount } from 'svelte';

	onMount(async () => {
		await import('@tylertech/forge/esm/autocomplete');
		await import('@tylertech/forge/esm/icon-button');
		await import('@tylertech/forge/esm/text-field');
		await import('@tylertech/forge/esm/select');
		await import('@tylertech/forge/esm/checkbox');
		await import('@tylertech/forge/esm/radio');
	});
</script>

<svelte:head>
	<title>Forge Accessibility Demo Site - Forms</title>
</svelte:head>

<div class="page-container">
	<forge-card class="card-container">
		<forge-toolbar>
			<forge-stack slot="before-start" inline alignment="center" gap="0">
				<div>
					<forge-icon-button aria-label="Navigate back">
						<forge-icon name="arrow_back" external></forge-icon>
					</forge-icon-button>
					<forge-tooltip>Navigate back</forge-tooltip>
				</div>
				<h2 class="forge-typography--heading4">Forms page</h2>
			</forge-stack>
			<forge-stack inline alignment="center" slot="end" gap="0">
				<div>
					<forge-icon-button aria-label="This describes the action of the icon button">
						<forge-icon name="bolt" external></forge-icon>
					</forge-icon-button>
					<forge-tooltip>This describes the action of the icon button</forge-tooltip>
				</div>
				<div>
					<forge-icon-button aria-label="Preview">
						<forge-icon name="preview" external></forge-icon>
					</forge-icon-button>
					<forge-tooltip>Preview something</forge-tooltip>
				</div>
				<div>
					<forge-icon-button aria-label="View more items">
						<forge-icon name="more_vert" external></forge-icon>
					</forge-icon-button>
					<forge-tooltip>View more items</forge-tooltip>
				</div>
			</forge-stack>
		</forge-toolbar>
		<div class="padding-16">
			<form autocomplete="off">
				<forge-stack>
					<forge-text-field label-position="block-start">
						<label for="first-name">First name</label>
						<input type="text" id="first-name" autocomplete="given-name" />
					</forge-text-field>
					<forge-text-field label-position="block-start">
						<label for="last-name">Last name</label>
						<input type="text" id="last-name" autocomplete="family-name" />
					</forge-text-field>
					<IconPickerAutocomplete />
				</forge-stack>
			</form>
		</div>
	</forge-card>
</div>

<style lang="scss">
	.page-container {
		max-width: 768px;
		margin: 24px auto;
	}

	.card-container {
		--forge-card-padding: 0;
	}
</style>
