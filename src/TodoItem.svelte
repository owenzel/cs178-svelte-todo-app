<script>
    // #component: slide (imported from a Svelte library)
	import { slide } from "svelte/transition";
    // #component: elasticInOut (imported from a Svelte library)
	import { elasticInOut } from "svelte/easing";

    // #variable: todos
    export let todos;
    // #variable: todo
    export let todo;

    function removeTodo(id) {
		// #controlFlow: findIndex method implicitly loops over the todos objects to find a todo with a matching id
		const index = todos.findIndex(the_todo => the_todo.id === id);
		todos.splice(index, 1);
		// #reactiveValues: setting todos triggers a view update so that we see an updated list of todos (without the removed one)
		todos = todos;
	}
</script>

<li class="list-item" transition:slide="{{duration: 300, easing: elasticInOut}}">
    <div class="is-flex" style="align-items: center">
        <span class="is-pulled-left">{todo.text}</span>
        <div style="flex: 1"></div>
        <button class="button is-text is-pulled-right is-small" on:click={()=> removeTodo(todo.id)}>
            <span class="icon">
                <i class="fas fa-check"></i>
            </span>
        </button>
    </div>
</li>