<script>
	import { onMount } from 'svelte';

	let currentQuote = '';
	let currentAuthor = '';
	let isLoading = true;

	const quotes = [
		{
			text: "Hidup tidak selalu menuntut kita untuk menjadi yang terbaik, tetapi menuntut kita untuk tetap bertahan dan belajar dari setiap proses yang menyakitkan.",
			author: "Refleksi Hidup"
		},
		{
			text: "Kedewasaan bukan tentang seberapa banyak yang kita miliki, melainkan seberapa bijak kita menerima kehilangan.",
			author: "Kebijaksanaan"
		},
		{
			text: "Tidak semua luka harus terlihat untuk membuktikan bahwa kita pernah berjuang dengan sepenuh hati.",
			author: "Perjuangan"
		},
		{
			text: "Waktu tidak menyembuhkan segalanya, tetapi ia mengajarkan kita bagaimana berdamai dengan kenyataan.",
			author: "Waktu"
		},
		{
			text: "Terkadang, langkah paling berani dalam hidup adalah memilih untuk tidak menyerah saat segalanya terasa tidak adil.",
			author: "Keberanian"
		},
		{
			text: "Hidup menguji kita bukan untuk menjatuhkan, melainkan untuk melihat seberapa kuat kita bangkit setelah jatuh.",
			author: "Ketangguhan"
		},
		{
			text: "Kesuksesan sejati bukan saat orang lain mengakui kita, tetapi saat kita mampu menghargai diri sendiri.",
			author: "Kesuksesan"
		},
		{
			text: "Setiap orang memiliki perjalanan hidupnya masing-masing; membandingkan diri hanya akan membuat kita lupa bersyukur.",
			author: "Syukur"
		},
		{
			text: "Diam bukan berarti kalah, terkadang itu adalah bentuk kebijaksanaan tertinggi dalam menghadapi dunia.",
			author: "Kebijaksanaan"
		},
		{
			text: "Kehidupan mengajarkan bahwa kehilangan bukan akhir, melainkan awal dari pemahaman yang lebih dalam tentang arti memiliki.",
			author: "Kehilangan"
		},
		{
			text: "Allah tidak membebani seseorang melainkan sesuai dengan kesanggupannya. Setiap ujian yang datang bukan tanda kelemahan kita, melainkan bukti bahwa Allah mengetahui batas kemampuan hamba-Nya.",
			author: "QS. Al-Baqarah: 286"
		},
		{
			text: "Sesungguhnya bersama kesulitan ada kemudahan. Kesulitan dan kemudahan berjalan berdampingan; tugas kita adalah tetap bertahan sampai pertolongan itu tiba.",
			author: "QS. Al-Insyirah: 6"
		},
		{
			text: "Sesungguhnya Aku dekat. Saat doa terasa sunyi, ingatlah bahwa Allah lebih dekat daripada yang kita bayangkan.",
			author: "QS. Al-Baqarah: 186"
		},
		{
			text: "Barang siapa bertawakal kepada Allah, maka Allah akan mencukupinya. Ketika manusia mengecewakan, tawakal mengajarkan kita bahwa cukup Allah sebagai sandaran.",
			author: "QS. At-Talaq: 3"
		},
		{
			text: "Ingatlah, hanya dengan mengingat Allah hati menjadi tenang. Ketenangan sejati bukan datang dari dunia, melainkan dari hati yang selalu terhubung dengan Allah.",
			author: "QS. Ar-Ra'd: 28"
		}
	];

	function getRandomQuote() {
		const randomIndex = Math.floor(Math.random() * quotes.length);
		const quote = quotes[randomIndex];
		currentQuote = quote.text;
		currentAuthor = quote.author;
		isLoading = false;
	}

	onMount(() => {
		getRandomQuote();
	});
</script>

<div class="card-base p-6">
	<div class="flex items-center gap-3 mb-4">
		<span class="text-[var(--primary)] text-xl transition">✨</span>
		<div class="text-sm font-bold text-neutral-400 transition">Daily Quote</div>
	</div>
	
	{#if !isLoading}
		<div class="mb-4">
			<p class="text-neutral-300 italic text-sm leading-relaxed transition">
				"{currentQuote}"
			</p>
			<p class="text-right text-xs text-[var(--primary)] mt-3 font-semibold transition">
				— {currentAuthor}
			</p>
		</div>
		
		<button 
			on:click={getRandomQuote}
			class="btn-regular w-full rounded-lg h-9 text-sm font-medium active:scale-95 transition"
			aria-label="Get random quote"
		>
			<span class="text-[0.875rem]">🔄</span>
			New Quote
		</button>
	{:else}
		<div class="animate-pulse">
			<div class="h-4 bg-neutral-700 rounded mb-2"></div>
			<div class="h-4 bg-neutral-700 rounded w-3/4"></div>
		</div>
	{/if}
</div>

<style>
	:global(.btn-regular) {
		display: flex;
		align-items: center;
		justify-content: center;
		gap: 0.5rem;
	}
</style>
