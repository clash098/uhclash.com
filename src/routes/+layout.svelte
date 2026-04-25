<script lang="ts">
    import '../app.css';
    let { children } = $props();
</script>

<svelte:head>
    <title>uhclash</title>
    <link rel="icon" href="/pfp.png" />
    <meta property="og:title" content="uhclash" />
    <meta property="og:description" content="a young developer from australia making cool stuff for vr games" />
    <meta property="og:image" content="https://uhclash.com/pfp.png" />
    <meta property="og:url" content="https://uhclash.com" />
    <meta property="og:type" content="website" />
</svelte:head>

{@render children()}