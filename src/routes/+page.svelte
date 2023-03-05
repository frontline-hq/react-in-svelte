<script lang="ts">
	import ReactWrapper from '$lib/ReactWrapper.svelte';
	import htm from 'htm/mini';
	import { h, type VNode } from 'preact';
	const html = htm.bind(h);

	const content1 = html`<div>This is a div</div>` as VNode;
	const content2 = html`<ul>
		<li>This is a list item</li>
	</ul>` as VNode;
	let content = content1;

	let timerId = setInterval(() => (content = content === content1 ? content2 : content1), 2000);

	const vNode = (content: any) => {
		return html`<div>${content}</div>` as VNode;
	};
</script>

<ReactWrapper vNode={vNode(content)} />
