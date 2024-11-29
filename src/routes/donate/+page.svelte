<script>
    let faqs = [
        {
            question: "Can I donate materials or printing?",
            answer: "Yes please!  We are currently using a printer that costs ~ $20 USD per deck.  Contact us!"
        },
        {
            question: "Do you have a GoFundMe?",
            answer: "Not yet - if you want to support the project you can PayPal or Zelle us directly."
        },
        {
            question: "Are you tax exempt?",
            answer: "Yes we are - we are an IRS recognized non-profit in the US.  Donations may be tax deductible."
        },
    ];

	let openFaqs = []; // track which FAQs are open

	const toggleFaq = (index) => {
		if (openFaqs.includes(index)) {
			openFaqs = openFaqs.filter(i => i !== index); // Close
		} else {
			openFaqs = [...openFaqs, index]; // Open
		}
	}
</script>

<div class="faq-container p-8">
    <h1 class="text-3xl font-bold mb-6 text-center">Donating to Playa Tarot</h1>

    <div class="faq-list">
        {#each faqs as faq, index}
            <div class="faq-item border-b border-gray-200 mb-4">
                <button
					class="faq-question w-full text-left py-4 px-6 text-lg font-medium text-gray-900 flex justify-between items-center focus:outline-none"
					on:click={() => toggleFaq(index)}
				>
                    {faq.question}
                    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6 transition-transform duration-200" class:rotate-180={openFaqs.includes(index)}>
						<path stroke-linecap="round" stroke-linejoin="round" d="M19.5 8.25l-7.5 7.5-7.5-7.5" />
					</svg>

                </button>
                {#if openFaqs.includes(index)}
                    <div class="faq-answer py-4 px-6 text-gray-700 transition-all duration-300 ease-in-out">
                        {@html faq.answer}
                    </div>
                {/if}
            </div>
        {/each}
    </div>
</div>


<div style="margin-left: 5%;">
<a href="/"><button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
  Back
</button></a>

</div>

<style>
/* You can add component-specific styles here if needed, or keep everything in Tailwind classes */
.faq-answer {

}

/* Additional styles for open/close animations, etc. */
</style>
