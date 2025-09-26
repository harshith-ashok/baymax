<script>
	let messages = [
		{ role: 'assistant', content: 'Hi, Im Baymax your personal healthcare assistant.' }
	];
	let input = '';

	async function sendMessage() {
		if (input.trim() === '') return;
		messages = [...messages, { role: 'user', content: input }];

		const userInput = input;
		input = '';

		try {
			const res = await fetch('http://localhost:8000/chat', {
				method: 'POST',
				headers: { 'Content-Type': 'application/json' },
				body: JSON.stringify({ message: userInput })
			});
			const data = await res.json();
			messages = [...messages, { role: 'assistant', content: data.reply }];
		} catch (e) {
			messages = [...messages, { role: 'assistant', content: "I'm sorry I didnt quite get that" }];
		}
	}
</script>

<div class="flex h-screen flex-col">
	<div class="flex-1 space-y-4 overflow-y-auto bg-gray-50 p-6">
		{#each messages as msg}
			<div class="flex {msg.role === 'user' ? 'justify-end' : 'justify-start'}">
				<div
					class="max-w-md rounded-lg px-4 py-2
                    {msg.role === 'user' ? 'bg-black text-white' : 'bg-red-200 text-gray-900'}"
				>
					{msg.content}
				</div>
			</div>
		{/each}
	</div>

	<form class="flex bg-white p-4" on:submit|preventDefault={sendMessage}>
		<button
			type="submit"
			class="btn px-4 py-2 btn-outline"
			on:click={window.location.reload}
			aria-label="delete"
			><svg
				xmlns="http://www.w3.org/2000/svg"
				width="16"
				height="16"
				fill="currentColor"
				class="bi bi-trash3"
				viewBox="0 0 16 16"
			>
				<path
					d="M6.5 1h3a.5.5 0 0 1 .5.5v1H6v-1a.5.5 0 0 1 .5-.5M11 2.5v-1A1.5 1.5 0 0 0 9.5 0h-3A1.5 1.5 0 0 0 5 1.5v1H1.5a.5.5 0 0 0 0 1h.538l.853 10.66A2 2 0 0 0 4.885 16h6.23a2 2 0 0 0 1.994-1.84l.853-10.66h.538a.5.5 0 0 0 0-1zm1.958 1-.846 10.58a1 1 0 0 1-.997.92h-6.23a1 1 0 0 1-.997-.92L3.042 3.5zm-7.487 1a.5.5 0 0 1 .528.47l.5 8.5a.5.5 0 0 1-.998.06L5 5.03a.5.5 0 0 1 .47-.53Zm5.058 0a.5.5 0 0 1 .47.53l-.5 8.5a.5.5 0 1 1-.998-.06l.5-8.5a.5.5 0 0 1 .528-.47M8 4.5a.5.5 0 0 1 .5.5v8.5a.5.5 0 0 1-1 0V5a.5.5 0 0 1 .5-.5"
				/>
			</svg></button
		>
		<input
			type="text"
			bind:value={input}
			placeholder="Type your message..."
			autofocus
			class="input-outline mx-2 w-full input-ghost border-black focus:border-1"
		/>
		<button type="submit" class="btn px-4 py-2 btn-outline">Send</button>
	</form>
</div>
