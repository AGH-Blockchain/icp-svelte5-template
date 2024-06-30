<script>
	import { backend } from '$lib/canisters';

	let greeting = '';

	function onSubmit(event) {
		const name = event.target.name.value;
		backend.greet(name).then((response) => {
			greeting = response;
		});
		return false;
	}
</script>

<main class="flex flex-col items-center justify-center min-h-screen">
	<form
		action="#"
		class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4 w-full max-w-xs"
		on:submit|preventDefault={onSubmit}
	>
		<label for="name" class="block text-gray-700 font-bold mb-2">Enter your name: &nbsp;</label>
		<input
			id="name"
			class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline mb-4"
			alt="Name"
			type="text"
		/>

		<button
			type="submit"
			class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-full"
			>Click Me!</button
		>
	</form>

	<section id="greeting" class="mt-4 font-bold text-xl mb-2">{greeting}</section>
</main>
