<script>
    import { onMount } from 'svelte';

    // Everything this section says lives here. Swap the placeholders for real copy;
    // set `photo` to an image path (e.g. '/founder.jpg' in /static) to replace the monogram.
    const founder = {
        name: 'AHMAD', // TODO: full name
        role: 'FOUNDER', // TODO: e.g. 'FOUNDER & PRINCIPAL ENGINEER'
        photo: '',
        bio: [
            // TODO: replace with your own words
            'QUINAS started from a simple conviction: software should be engineered with the same intent as architecture. Every layer considered, nothing added for show.',
            'I lead every engagement directly, from the first system diagram to the last deploy.'
        ],
        quote: 'Stripped of noise. Calculated by design.',
        facts: [
            { label: 'ROLE', value: 'Founder' },
            { label: 'BASE', value: 'Zamboanga' },
            { label: 'DISCIPLINE', value: 'Product Engineering' }
        ],
        /** @type {{ label: string, href: string }[]} */
        links: [
            // TODO: e.g. { label: 'LINKEDIN', href: 'https://linkedin.com/in/…' }
        ]
    };

    let live = $state(false);
    let sectionEl = $state();

    onMount(() => {
        if (typeof IntersectionObserver === 'undefined') {
            live = true;
            return;
        }
        const io = new IntersectionObserver(
            ([entry]) => {
                if (entry.isIntersecting) {
                    live = true;
                    io.disconnect();
                }
            },
            { threshold: 0.15 }
        );
        io.observe(sectionEl);
        return () => io.disconnect();
    });
</script>

<svelte:head>
    <!-- Fail-open: without JS, show the section rather than leaving it blank -->
    <noscript><style>.founder-root .reveal { opacity: 1 !important; transform: none !important; }</style></noscript>
</svelte:head>

<section
    id="founder"
    bind:this={sectionEl}
    class:is-live={live}
    class="founder-root w-full bg-black text-zinc-300 border-t border-zinc-900 select-none font-mono"
>
    <!-- Section Header -->
    <div class="h-20 md:h-24 border-b border-zinc-800/60 flex items-center justify-between gap-4 px-5 sm:px-8 md:px-16">
        <div class="flex items-center gap-2">
            <span class="w-1.5 h-1.5 rounded-full bg-zinc-100 opacity-80 shadow-[0_0_8px_rgba(255,255,255,0.5)]"></span>
            <span class="w-1.5 h-1.5 rounded-full bg-zinc-100 opacity-50"></span>
            <span class="w-1.5 h-1.5 rounded-full bg-zinc-100 opacity-30"></span>
        </div>
        <span class="text-base sm:text-xl md:text-2xl tracking-wider md:tracking-widest text-white">THE FOUNDER</span>
    </div>

    <div class="max-w-7xl mx-auto grid grid-cols-1 lg:grid-cols-12 gap-12 lg:gap-16 px-5 sm:px-8 md:px-16 py-16 md:py-24">

        <!-- Portrait Frame -->
        <figure class="reveal lg:col-span-5 w-full max-w-60 sm:max-w-sm mx-auto lg:max-w-none" style="--d: 0ms;">
            <div class="relative aspect-square sm:aspect-4/5 border border-zinc-800 bg-zinc-950 overflow-hidden">
                {#if founder.photo}
                    <img src={founder.photo} alt={founder.name} class="absolute inset-0 w-full h-full object-cover grayscale contrast-110" loading="lazy" />
                {:else}
                    <!-- Monogram fallback until a photo is supplied -->
                    <div class="absolute inset-0 opacity-[0.07] bg-[linear-gradient(#fff_1px,transparent_1px),linear-gradient(90deg,#fff_1px,transparent_1px)] bg-size-[32px_32px]"></div>
                    <div class="absolute inset-0 flex items-center justify-center">
                        <span class="font-sans font-bold text-[7rem] sm:text-[11rem] leading-none text-white/90 tracking-tight">{founder.name.charAt(0)}</span>
                    </div>
                {/if}

                <!-- Registration corners -->
                <span class="absolute top-3 left-3 w-3 h-3 border-t border-l border-zinc-500"></span>
                <span class="absolute top-3 right-3 w-3 h-3 border-t border-r border-zinc-500"></span>
                <span class="absolute bottom-3 left-3 w-3 h-3 border-b border-l border-zinc-500"></span>
                <span class="absolute bottom-3 right-3 w-3 h-3 border-b border-r border-zinc-500"></span>
            </div>
            <figcaption class="mt-3 flex justify-between text-[10px] tracking-[0.2em] text-zinc-600">
                <span>// FILE 001</span>
                <span>{founder.role}</span>
            </figcaption>
        </figure>

        <!-- Profile -->
        <div class="lg:col-span-7 flex flex-col justify-center">
            <span class="reveal text-[10px] tracking-[0.3em] text-zinc-500" style="--d: 150ms;">// PRINCIPAL</span>

            <h2 class="reveal mt-4 font-sans font-bold text-5xl sm:text-6xl md:text-7xl tracking-tight text-white leading-none" style="--d: 250ms;">
                {founder.name}
            </h2>
            <p class="reveal mt-4 text-xs tracking-[0.3em] text-[#EAB308]" style="--d: 350ms;">{founder.role}</p>

            <div class="reveal mt-10 space-y-5 max-w-xl font-sans text-base md:text-lg font-light leading-relaxed text-zinc-400" style="--d: 450ms;">
                {#each founder.bio as para, i (i)}
                    <p>{para}</p>
                {/each}
            </div>

            <blockquote class="reveal mt-10 border-l border-zinc-700 pl-5 font-sans text-lg md:text-xl text-zinc-100 font-light" style="--d: 550ms;">
                “{founder.quote}”
            </blockquote>

            <dl class="reveal mt-12 grid grid-cols-1 sm:grid-cols-3 border-t border-zinc-800" style="--d: 650ms;">
                {#each founder.facts as fact (fact.label)}
                    <div class="py-4 sm:pr-6 border-b sm:border-b-0 border-zinc-900">
                        <dt class="text-[10px] tracking-[0.2em] text-zinc-600">{fact.label}</dt>
                        <dd class="mt-1 text-sm text-zinc-200">{fact.value}</dd>
                    </div>
                {/each}
            </dl>

            {#if founder.links.length}
                <div class="reveal mt-8 flex flex-wrap gap-x-6 gap-y-3 text-[11px] tracking-widest" style="--d: 750ms;">
                    {#each founder.links as link (link.href)}
                        <a href={link.href} target="_blank" rel="noopener noreferrer" class="text-zinc-400 hover:text-white transition-colors duration-300">// {link.label} ↗</a>
                    {/each}
                </div>
            {/if}
        </div>
    </div>
</section>

<style>
    .founder-root :global(.reveal) {
        opacity: 0;
        transform: translateY(12px);
        transition:
            opacity 900ms cubic-bezier(0.16, 1, 0.3, 1),
            transform 900ms cubic-bezier(0.16, 1, 0.3, 1);
        transition-delay: var(--d, 0ms);
    }

    .is-live :global(.reveal) {
        opacity: 1;
        transform: none;
    }

    @media (prefers-reduced-motion: reduce) {
        .founder-root :global(.reveal) {
            opacity: 1;
            transform: none;
            transition: none;
        }
    }
</style>
