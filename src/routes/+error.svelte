<script lang="ts">
    import { page } from '$app/state';
</script>

<div class="flex h-screen w-screen items-center justify-center">
    <div class="flex flex-col items-center gap-6 text-center px-6">
        <img src="/sad_clash_profile.png" alt="error" class="h-40 w-40 rounded-full" />
        <h1 class="text-5xl sm:text-7xl font-bold">{page.status}</h1>
        <p class="max-w-xl text-2xl text-zinc-800 dark:text-zinc-200">
            {page.error?.message ?? 'something went wrong'} :c
        </p>
    </div>
</div>