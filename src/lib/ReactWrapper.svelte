<script lang="ts">
	import { render as preactRender, hydrate as preactHydrate, type VNode } from 'preact';
	import { render as preactPrerender } from 'preact-render-to-string';
	export let vNode: VNode;

	const prerendered = preactPrerender(vNode as VNode<{}>);

	function hydrate(node: HTMLElement, vNode: VNode) {
		node.innerHTML = prerendered;
		preactHydrate(vNode, node);
		return {
			update(vNode: VNode) {
				preactHydrate(vNode, node);
			},
			destroy() {
				preactRender(null, node);
			}
		};
	}
</script>

<div use:hydrate={vNode} />
