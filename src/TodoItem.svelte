<script>
    export let todoText;
    const todoDone = (e) => {
        todoText = `<strike>${todoText}<strike>`
    }
</script>

<div>
    <p>{@html todoText}</p>
    <button on:click={todoDone}>done</button>
</div>