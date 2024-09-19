<script lang="ts">
	import { type NodeProps } from '@xyflow/svelte';

	type Data = { message: string };
	type $$Props = NodeProps & { data: Data };

	export let id: string;
	export let data: Data;
	const { message } = data;

	const bgColor: string = id == 'node0' ? 'pink' : id == 'node1' ? 'lightgreen' : 'lightblue';
</script>

<div style:background-color={bgColor}>
	{message}
</div>
