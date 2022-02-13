<script lang="ts">
	import TextField from '@smui/textfield';
	import HelperText from '@smui/textfield/helper-text';

	export let address: string | null = null;
	let focused = false;
	$: invalid = !focused && address !== null && (address.length !== 52 || !address.startsWith('9'));
</script>

<TextField
	label="Wallet Address"
	bind:value={address}
	bind:invalid
	on:focus={() => (focused = true)}
	on:blur={() => (focused = false)}
	style="min-width: 500px;"
>
	<HelperText validationMsg slot="helper">That's not a valid Ergo P2PK address.</HelperText>
</TextField>
