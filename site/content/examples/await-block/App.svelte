<script>
	let promise;

	function findAnswer() {
		promise = new Promise(fulfil => {
			const delay = 1000 + Math.random() * 3000;
			setTimeout(() => fulfil(42), delay);
		});
	}
</script>

<button on:click='{findAnswer}'>find the answer</button>

{#if promise}
	{#await promise}
		<p>wait for it...</p>
	{:then answer}
		<p>the answer is {answer}!</p>
	{:catch error}
		<p>well that's odd</p>
	{/await}
{/if}
