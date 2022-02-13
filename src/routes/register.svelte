<script lang="ts">
	import AddressInput from '$lib/registration/AddressInput.svelte';

	import FormField from '@smui/form-field';
	import Radio from '@smui/radio';

	let address: string | null = null;
	let allowV1Pools: boolean = false;
</script>

<h2>Registration</h2>
<p>
	Note that registering is not required to run an oracle core, but it will make you more visible to
	pool creators and allow them to recruit you.
</p>
<p>
	By running an oracle you will be providing key infrastructure. Pools rely on selected oracles that
	cannot be changed after launch. Oracles therefore take on a certain responsibily and moral
	commitment. Please refrain from joining a pool if all you want is to test the waters. Testnets
	exist for a reason.
</p>
<p>
	To mitigate spamming and as a token of commitment, we ask for a symbolic registration fee of 1
	ERG. Collected funds will be used to support community projects.
</p>

<div>
	<AddressInput bind:address />

	<FormField style="margin-right: 1em;">
		<Radio bind:group={allowV1Pools} value={true} />
		<span slot="label">Allow V1 pools</span>
	</FormField>
	<FormField style="margin-right: 1em;">
		<Radio bind:group={allowV1Pools} value={false} />
		<span slot="label">V2 pools only</span>
	</FormField>
</div>
<pre>Your address is: {address}, V1 pools: {allowV1Pools}</pre>
