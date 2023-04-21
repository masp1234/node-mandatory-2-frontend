<script>
    export let actionEndpoint;
    export let submitBtnText = 'Submit'
    export let fields = []
</script>

<form action="{actionEndpoint}" method="POST">
    {#each fields as field}
    <label for="{field.id}">{field.labelText}</label>
    <input type="text" id="{field.id}" placeholder="{field.placeholder}">
    {/each}
    
    <div class="button-container">
        <button type="submit">{submitBtnText}</button>
    </div>
    
</form>

<style>
    form {
        display: flex;
        flex-direction: column;
        width: 30%;
    }
    label {
        margin-bottom: 0.5em;
    }
    input {
        margin-bottom: 1em;
        padding: 0.5em;
        border-radius: 0.5em;
    }
    .button-container {
        display: flex;
        justify-content: center;

    }
    button {
        background-color: rgb(35, 182, 35);
        border-style: none;
        color: white;
    }
</style>