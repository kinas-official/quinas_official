<script>
    import Intro from '$lib/components/Intro.svelte';
	import Manifesto from '$lib/components/Manifesto.svelte';
    import Ecosystem from '$lib/components/Ecosystem.svelte';
	import Systems from '$lib/components/Systems.svelte';
	import Beliefs from '$lib/components/Beliefs.svelte';
	import Ledger from '$lib/components/Ledger.svelte';
	import Founder from '$lib/components/Founder.svelte';
	import ContactTerminal from '$lib/components/ContactTerminal.svelte';
	import Footer from '$lib/components/Footer.svelte';
	import { page } from '$app/state';

	const title = 'QUINAS — Systems Engineered With Intent';
	const description =
		'Product engineering studio building high-fidelity digital infrastructure — stripped of noise, calculated by design.';
	// Crawlers require an absolute og:image URL
	const ogImage = $derived(`${page.url.origin}/og.png`);
</script>

<svelte:head>
	<title>{title}</title>
	<meta name="description" content={description} />

	<meta property="og:type" content="website" />
	<meta property="og:site_name" content="QUINAS" />
	<meta property="og:title" content={title} />
	<meta property="og:description" content={description} />
	<meta property="og:url" content={page.url.href} />
	<meta property="og:image" content={ogImage} />
	<meta property="og:image:width" content="1200" />
	<meta property="og:image:height" content="630" />
	<meta property="og:image:alt" content="QUINAS — Systems Engineered With Intent" />

	<meta name="twitter:card" content="summary_large_image" />
	<meta name="twitter:title" content={title} />
	<meta name="twitter:description" content={description} />
	<meta name="twitter:image" content={ogImage} />
</svelte:head>

<Intro />
<Manifesto />
<Ecosystem />
<Systems />
<Beliefs />
<Ledger />
<Founder />
<ContactTerminal />
<Footer />