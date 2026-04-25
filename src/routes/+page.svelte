<script>
    import { onMount } from 'svelte';

    let time = $state('');
    let emoji = $state('');

    onMount(() => {
        const update = () => {
            const fmt = new Intl.DateTimeFormat('en-AU', {
                timeZone: 'Australia/Sydney',
                hour: 'numeric',
                minute: '2-digit',
                hour12: true,
                weekday: 'short'
            });

            const parts = Object.fromEntries(fmt.formatToParts(new Date()).map(p => [p.type, p.value]));
            const hour24 = new Intl.DateTimeFormat('en-AU', { timeZone: 'Australia/Sydney', hour: 'numeric', hour12: false }).format(new Date());
            const minutePart = new Intl.DateTimeFormat('en-AU', { timeZone: 'Australia/Sydney', minute: 'numeric' }).format(new Date());

            const hour = parseInt(hour24);
            const minute = parseInt(minutePart);
            const totalMinutes = hour * 60 + minute;
            const isWeekday = !['Sat', 'Sun'].includes(parts.weekday);

            if (totalMinutes < 7 * 60) {
                emoji = '😴';
            } else if (isWeekday && totalMinutes >= 8 * 60 && totalMinutes < 15 * 60 + 30) {
                emoji = '🏫';
            } else {
                emoji = '☀️';
            }

            time = new Intl.DateTimeFormat('en-AU', {
                timeZone: 'Australia/Sydney',
                weekday: 'long',
                hour: '2-digit',
                minute: '2-digit',
                hour12: true
            }).format(new Date());
        };
        update();
        const interval = setInterval(update, 1000);
        return () => clearInterval(interval);
    });
</script>

<div class="flex h-screen w-screen items-center justify-center">
    <div class="flex flex-col items-center gap-6 text-center px-6">
        <img src="/pfp.png" alt="clash" class="h-40 w-40 rounded-full" />
        <h1 class="typewriter text-5xl sm:text-7xl font-bold">hi, im clash.</h1>
        <p class="text-sm text-zinc-500 dark:text-zinc-400">{emoji} {time}</p>
        <p class="max-w-xl text-2xl text-zinc-800 dark:text-zinc-200">
            a young developer from australia making cool stuff for vr games like
            <a href="https://oriondriftvr.com/" target="_blank" class="underline decoration-zinc-400 dark:decoration-zinc-500 hover:opacity-70 transition-opacity">orion drift</a>
            and
            <a href="https://www.gorillatagvr.com/" target="_blank" class="underline decoration-zinc-400 dark:decoration-zinc-500 hover:opacity-70 transition-opacity">gorilla tag</a>.
        </p>
        <div class="flex gap-6 mt-2">
            <a href="https://github.com/clash098" target="_blank" class="hover:opacity-60 transition-opacity">
                <img src="https://cdn.simpleicons.org/github/000000" alt="github" class="h-9 w-9 dark:invert" />
            </a>
            <a href="https://buymeacoffee.com/uhclash" target="_blank" class="hover:opacity-60 transition-opacity">
                <img src="https://cdn.simpleicons.org/buymeacoffee/000000" alt="buymeacoffee" class="h-9 w-9 dark:invert" />
            </a>
            <a href="mailto:contact@uhclash.com" class="hover:opacity-60 transition-opacity">
                <img src="https://cdn.simpleicons.org/gmail/000000" alt="email" class="h-9 w-9 dark:invert" />
            </a>
        </div>
    </div>
</div>