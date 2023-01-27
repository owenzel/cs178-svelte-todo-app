<script>
	// #component: slide (imported from a Svelte library)
	import { slide } from "svelte/transition";
    	// #component: elasticInOut (imported from a Svelte library)
	import { elasticInOut } from "svelte/easing";

	import Form from "./Form.svelte";
	import TodoItem from "./TodoItem.svelte";

	// #variable: todos
	let todos = [];
	// #variable: input
	let input = "";
</script>

<svelte:head>
	<!-- Import the Bulma CSS Framework for general styling -->
	<link rel="stylesheet" type="text/css" href="https://cdn.jsdelivr.net/npm/bulma@0.8.0/css/bulma.min.css"/>
	<!-- Import the Font Awesome library for icons -->
	<script src="https://use.fontawesome.com/releases/v5.3.1/js/all.js"></script>
</svelte:head>
<main class="container is-fluid">
	<div class="columns is-centered is-vcentered is-mobile">
		<div class="column is-narrow" style="width: 70%">
			<br/>
			<h1 class="has-text-centered title">Svelte TODO</h1>
			<!-- #component: Form (defined in Form.svelete and imported here) -->
			<!-- #properties: input is passed from parent App component to child Form component, with two-way binding -->
			<!-- #properties: todos is passed from parent App component to child Form component, with two-way binding -->
			<Form bind:input bind:todos/>
			<ul class:list={todos.length > 0}>
				<!-- #controlFlow: #each iterates over todos -->
				{#each todos as todo (todo.id)}
					<!-- #component: TodoItem (defined in TodoItem.svelete and imported here) -->
					<!-- #properties: todos is passed from parent App component to child TodoItem component, with two-way binding -->
					<!-- #properties: todo is passed from parent App component to child TodoItem component -->
					<TodoItem bind:todos todo={todo}/>
				{:else}
					<li class="has-text-centered" transition:slide="{{duration: 300, easing: elasticInOut}}">
						Nothing here!
					</li>
				{/each}
			</ul>
		</div>
	</div>
</main>
