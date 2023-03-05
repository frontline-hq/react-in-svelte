<script lang="ts">
	import { render as preactRender, hydrate as preactHydrate, type VNode } from 'preact';
	import { render as preactPrerender } from 'preact-render-to-string';
	export let vNode: VNode;

	$: prerendered = preactPrerender(vNode as VNode<{}>);

	function hydrate(
		node: HTMLElement,
		{ vNode, prerendered }: { vNode: VNode; prerendered: string }
	) {
		node.innerHTML = prerendered;
		preactHydrate(vNode, node);
		return {
			// Do I need to update here?
			destroy() {
				preactRender(null, node);
			}
		};
	}
</script>

<div use:hydrate={{ vNode, prerendered }} />
