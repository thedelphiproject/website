<script lang="ts">
	import AddressInput from '$lib/registration/AddressInput.svelte';
	import SegmentedButton, { Segment } from '@smui/segmented-button';
	import { Label } from '@smui/common';

	import Button from '@smui/button';
	import Checkbox from '@smui/checkbox';
	import FormField from '@smui/form-field';
	import Paper, { Title, Subtitle, Content } from '@smui/paper';

	let addressOptions: string[] = ['Manual', 'Nautilus'];
	let selectedAddressOption: string = addressOptions[1];
	let address: string | null = null;
	let allowV1Pools: boolean = false;

	let ergoConnectorNotFound = null;
	let connected: boolean = false;
	let balance: BigInteger = null;

	function connectWallet() {
		if (typeof ergoConnector === 'undefined') {
			ergoConnectorNotFound = true;
			return;
		}
		ergoConnectorNotFound = false;
		ergoConnector.nautilus.connect().then((access_granted) => {
			if (access_granted) {
				connected = true;
				// Read balance to confirm there's enough to cover the fee.
				ergo.get_balance().then(function (bal) {
					balance = bal;
				});
				// Take first unused address for now.
				// TODO: Let user pick address
				ergo.get_unused_addresses().then(function (addresses) {
					address = addresses[0];
				});
			} else {
				connected = false;
			}
		});
	}
</script>

<h2>Registration</h2>

<p>
	Note that registering is not required to run an oracle core, but it will make you more visible to
	pool creators and allow them to recruit you.
</p>
<p>
	To mitigate spamming and as a token of commitment, we ask for a symbolic registration fee of 1
	ERG. Collected funds will be used to support community projects.
</p>
<Paper style="background-color: #F3EBFE;">
	<Title>On becoming an oracle</Title>
	Pools rely on a selection of oracles that cannot be changed after launch. Oracles therefore take on
	a certain responsibility by providing key infrastructure. If you are unsure and want to test the waters
	for some time, use the testnet first.
</Paper>

<div class="registration-form">
	<div class="centered">
		<SegmentedButton
			segments={addressOptions}
			let:segment
			singleSelect
			bind:selected={selectedAddressOption}
		>
			<Segment {segment}>
				<Label>{segment}</Label>
			</Segment>
		</SegmentedButton>
	</div>
	<FormField>
		<Checkbox bind:checked={allowV1Pools} />
		<span slot="label">Accept V1 pools</span>
	</FormField>
	<AddressInput bind:address disabled={selectedAddressOption !== 'Manual'} />
	<div id="wallet-wrapper" class="centered">
		{#if selectedAddressOption === 'Nautilus'}
			<Button on:click={connectWallet} variant="outlined" style="max-width: 200px;"
				><Label>Connect wallet</Label></Button
			>
			{#if ergoConnectorNotFound}
				<p>Enable Nautilus for this page</p>
			{/if}
		{/if}
	</div>
</div>

<div class="right">
	<Button on:click={() => null} variant="raised" style="max-width: 100px;" disabled
		><Label>Register</Label></Button
	>
</div>

<div class="address-form" />

<style>
	.registration-form {
		display: flex;
		flex-direction: column;
		row-gap: 1em;
		border: 1px solid gray;
		border-radius: 5px;
		margin-bottom: 2em;
		padding: 1.5em;
		margin-top: 2em;
	}
	.centered {
		display: flex;
		flex-direction: column;
		align-items: center;
	}
	.right {
		display: flex;
		justify-content: center;
	}
	#wallet-wrapper {
		min-height: 37px;
	}
</style>
