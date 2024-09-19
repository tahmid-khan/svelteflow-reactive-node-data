<script lang="ts">
	import { writable, type Writable } from 'svelte/store';
	import { SvelteFlow, Background } from '@xyflow/svelte';
	import type { Edge, Node, NodeTypes } from '@xyflow/svelte';
	import CustomNode from '$lib/CustomNode.svelte';

	import '@xyflow/svelte/dist/style.css';

	/**
	 * Current time (integer) in the simulation
	 */
	let time: number = 0;

	/**
	 * Table of timestamped messages; structure: `<time>: { <node ID>: <message> }`
	 */
	const messages: Record<number, Record<string, string>> = {
		0: {
			'node0': 'node0: time = 0',
			'node1': 'node1: time = 0',
			'node2': 'node2: time = 0'
		},
		1: {
			'node0': 'node0: time = 1',
			'node1': 'node1: time = 1',
			'node2': 'node2: time = 1'
		},
		2: {
			'node0': 'node0: time = 2',
			'node1': 'node1: time = 2',
			'node2': 'node2: time = 2'
		},
		3: {
			'node0': 'node0: time = 3',
			'node1': 'node1: time = 3',
			'node2': 'node2: time = 3'
		},
		4: {
			'node0': 'node0: time = 4',
			'node1': 'node1: time = 4',
			'node2': 'node2: time = 4'
		},
		5: {
			'node0': 'node0: time = 5',
			'node1': 'node1: time = 5',
			'node2': 'node2: time = 5'
		}
	};

	const initialNodes: Node[] = ['node0', 'node1', 'node2'].map((id) => {
		return {
			id,
			position: {
				x: Math.random() * 150,
				y: Math.random() * 150
			},
			data: {
				message: messages[time][id]
			},
			type: 'node'
		} satisfies Node;
	});

	const nodes: Writable<Node[]> = writable(initialNodes);
	const edges: Writable<Edge[]> = writable([]);
	const nodeTypes: NodeTypes = { node: CustomNode };
</script>

<main>
	<SvelteFlow {nodes} {edges} {nodeTypes} fitView>
		<Background />
	</SvelteFlow>
</main>

<style>
	main {
		height: 100vh;
		width: 150vh;
	}
</style>
