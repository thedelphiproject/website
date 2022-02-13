<script lang="ts">
	import TextField from '@smui/textfield';
	import HelperText from '@smui/textfield/helper-text';

	export let address: string | null = null;
	export let disabled = false;
	let focused = false;
	$: invalid = !focused && address !== null && (address.length !== 51 || !address.startsWith('9'));
</script>

<div>
	<TextField
		label="Wallet Address"
		bind:value={address}
		bind:invalid
		on:focus={() => (focused = true)}
		on:blur={() => (focused = false)}
		bind:disabled
		style="width: 100%;"
	>
		<HelperText validationMsg slot="helper">That's not a valid Ergo P2PK address.</HelperText>
	</TextField>
</div>
