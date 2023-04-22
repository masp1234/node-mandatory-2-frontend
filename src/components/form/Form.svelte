<script>
    import Link from "../link/Link.svelte";
    export let actionEndpoint;
    export let submitBtnText = 'Submit'
    export let fields = []
    export let links = []
    // button=submit ændrer på URL - fix det
</script>

<form action="{actionEndpoint}" method="POST">
    
    {#each fields as field}
    <label for="{field.id}">{field.labelText}</label>
    <input type="text" id="{field.id}" placeholder="{field.placeholder}">
    {/each}
    
    <div class="button-container">
        <button type="submit">{submitBtnText}</button>
    </div>

    {#if links}
    {#each links as link}
    <Link url={link.url} text={link.text}></Link>
    <br>
    {/each}
    {/if}

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
        margin: 1em 0em 1em 0em;

    }
    button {
        background-color: rgb(35, 182, 35);
        border-style: none;
        color: white;
    }
</style>