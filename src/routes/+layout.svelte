<script>
	export const prerender = true;
	import '../app.css';
	import Header from '../components/Header.svelte';
	import Footer from '../components/Footer.svelte';

	let scrollY;
	let innerHeight;
	let innerWidth;

	function goTop() {
		document.body.scrollIntoView({ behavior: 'smooth' });
	}
</script>

<div class="container relative flex flex-col max-w-[1400px] mx-auto w-full text-sm sm:text-base min-h-screen">
	<div
		class={`fixed bottom-0 w-full duration-200 flex p-10 z-[10] + ${
			scrollY > 0 ? 'opacity-full pointer-events-auto' : 'pointer-events-none opacity-0'
		}`}
	>
		<button on:click={goTop} class="ml-auto rounded-full bg-slate-900 text-violet-400 sm:px-4 hover:bg-slate-800 cursor-pointer">
			<i class="fa-solid fa-arrow-up grid place-items-center aspect-square" />
		</button>
	</div>
	<Header y={scrollY} />
	<slot />
	<Footer />
</div>

<svelte:window bind:scrollY bind:innerHeight bind:innerWidth />
