<script>
    import toastr from 'toastr'
    import Link from "../link/Link.svelte";
    export let endpoint;
    export let submitBtnText = 'Submit'
    export let fields = []
    export let links = []
    export let callback

    async function handleSubmit(event, callback) {
        event.preventDefault()
        const formData = new FormData(event.target)
        const response = await fetch(endpoint, {
            method: "POST",
            body: JSON.stringify(Object.fromEntries(formData)),
            headers: {
                "Content-Type": "application/json"
            }
        })
         callback(formData)
         const data = await response.json();
         toastr.options = {
            "positionClass": "toast-bottom-right",
         }
         response.status >= 400 ? toastr.error(data.message) : toastr.success(data.message)
        }

</script>

<form on:submit={event => {
    handleSubmit(event, callback)
}}>
    
    {#each fields as field}
    <label for="{field.id}">{field.labelText}</label>
    <input type={field.type ? field.type: "text"} id="{field.id}" name={field.id} placeholder="{field.placeholder}">
    {/each}

    
    <div id="lower-container">
        <div class="button-container">
            <button type="submit">{submitBtnText}</button>
        </div>
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
        font-weight: bold;
        font-size: 1.1em
    }
    input {
        margin-bottom: 1em;
        padding: 0.5em;
        border-radius: 0.5em;
        font-size: 1.01em;
    }
    .button-container {
        display: flex;
        justify-content: center;
        margin: 0em 0em 1em 0em;

    }
    button {
        background-color: rgb(42, 190, 42);
        border-style: none;
        color: white;
        border-radius: 8px;
        padding: 0.6em 1.2em;
        width: 8em;
    }
    button:hover {
        background-color: rgb(44, 146, 44);
    }
</style>