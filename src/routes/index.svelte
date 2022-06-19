<script>
	let newTodo = '';
	let todoList = [{ text: 'Write my first post', id: 'aaa', status: false }];

	let id = 0;
	const addTodoList = () => {
		todoList = [...todoList, { text: newTodo, id: 'a' + id, status: false }];
		id++;
		newTodo = '';
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
		<button type="submit" />
	</form>
	<br />

	{#each todoList as item}
		<div>
			<label for={item.id} class="cursor-pointer">
				<span class={item.status ? 'text-red-500 line-through' : 'text-green-500'}>{item.text}</span
				>
				<input class="hidden" id={item.id} type="checkbox" bind:checked={item.status} />
			</label>
		</div>
	{/each}
</main>
