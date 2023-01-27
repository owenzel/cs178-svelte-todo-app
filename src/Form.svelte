<script>
    // #variable: input
    export let input;
    // #variable: todos
    export let todos;

    function addTodo() {
		// #controlFlow: if statement
		if (input) {
			// #reactiveValues: setting todos triggers a view update so that we see an updated list of todos (without the new one)
			todos = [
				// #controlFlow: spread operator (...) expands the "todos" iteratable, with some implicit looping behavior
				...todos,
				{
					text: input,
					id: Math.random().toString(36).substr(2,9)
				}
			];
		}
		// #reactiveValues: setting input to the empty string triggers a view update so that the input box is blank again
		input = "";
	}
</script>

<form
    class="field has-addons"
    style="justify-content: center"
    on:submit|preventDefault="{addTodo}"
>
    <div class="control">
        <input bind:value="{input}" class="input" type="text" placeholder="TODO" />
    </div>
    <div class="control">
        <button class="button is-primary">
        <span class="icon is-small">
            <i class="fas fa-plus"></i>
        </span>
        </button>
    </div>
</form>