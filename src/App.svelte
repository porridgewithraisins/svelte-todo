<script>
    import { onMount } from "svelte";
    import TodoItem from "./TodoItem.svelte";

    let todos = [];
    let todoText = "";
    onMount(() => {
        const stored = localStorage.getItem("todos");
        todos = JSON.parse(stored) || [];
    });

    const addTodo = () => {
        todos = [...todos, todoText];
        localStorage.setItem("todos", JSON.stringify(todos));
    };
    const clear = () => {
        localStorage.removeItem("todos");
		todos = [];
    };
</script>

<main>
    {#each todos as todo}
        <TodoItem todoText={todo} />
    {/each}
    <button on:click={clear}>clear</button>
    <form on:submit|preventDefault={addTodo}>
        <input bind:value={todoText} />
        <input type="submit" value="add todo" />
    </form>
</main>
