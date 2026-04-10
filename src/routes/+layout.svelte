<script lang="ts">
    import '../app.css';
    let { children } = $props();
</script>

<svelte:head>
    <title>uhclash</title>
    <link rel="icon" href="/pfp.png" />
</svelte:head>

{@render children()}