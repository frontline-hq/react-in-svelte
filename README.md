# React in svelte

A library that enables you to use React components in Svelte - 6.8kB mified & gzipped 

It even utilizes SSR and hydration to reduce client side rendering work.

## Installation

`yarn add @frontline-hq/react-in-svelte` or `npm install @frontline-hq/react-in-svelte`

## Usage

Import our Wrapper in your application and pass a VNode to it. We recommend creating a VNode with htm.

```svelte
<script lang="ts">
    import {h, type VNode} from 'preact';
    import ReactWrapper from "@frontline-hq/react-in-svelte"
    import htm from "htm"
    import SomeComponent from "SomeComponentLibrary"

    const html = htm.bind(h)

    const props = {
        // a lot of props here
    }

    const vNode = html`
        <${SomeComponent} ...${props}>
            <div>Some more components here</div>
        <//>
    ` as VNode
</script>

<ReactWrapper {vNode} />
```

This will create a `<div></div>` within ReactWrapper to host the (p)react dom. The React components will then be inserted within the wrapper.

## Developing

Once you've created a project and installed dependencies with `npm install` (or `pnpm install` or `yarn`), start a development server:

```bash
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

## Building

To create a production version of your app:

```bash
npm run build
```

## Publishing

```bash
cd package
npm publish
```
