<script>
	const createID = () => `_${Math.random().toString().substring(2, 35)}`;
	let newTodo = '';
	let todoList = [{ text: 'Write my first post', id: 'aaa', status: false }];

	const addTodoList = () => {
		todoList = [...todoList, { text: newTodo, id: createID(), status: false }];
		newTodo = '';
	};
	const removeFromList = (id) => {
		todoList = todoList.filter((x) => x.id !== id);
	};
</script>

<main class="m-10">
	<h1 class="text-2xl">Learning SvelteKit</h1>
	<p>
		Visit <a class="text-blue-400 underline" href="https://kit.svelte.dev">kit.svelte.dev</a> to read
		the documentation
	</p>
	<h2 class="m-5">simple TODO</h2>
	<form on:submit|preventDefault={addTodoList}>
		<input
			class="border-solid border-2 rounded-sm"
			type="text"
			placeholder="New TODO"
			bind:value={newTodo}
		/>
	</form>
	<br />
	{#each todoList as item}
		<div>
			<label for={item.id} class="cursor-pointer">
				<span class={item.status ? 'text-red-500 line-through' : 'text-green-500'}>{item.text}</span
				>
				<input class="hidden" id={item.id} type="checkbox" bind:checked={item.status} />
			</label>
			<span class="cursor-pointer" on:click={() => removeFromList(item.id)}>❌</span>
		</div>
	{/each}
</main>
