<script>
    import toastr from 'toastr'
    import Link from "../link/Link.svelte";
    export let endpoint;
    export let submitBtnText = 'Submit'
    export let fields = []
    export let links = []
    export let callback = null

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
         const data = await response.json();
         if (callback) {
            callback(data, response.status)
        }
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
    {#if typeof field.tag === 'undefined' || field.tag.toLowerCase() === 'input'}
        <input type={field.type ? field.type : "text"} id="{field.id}" name={field.id} placeholder="{field.placeholder}">
    {:else if field.tag.toLowerCase() === 'textarea'}
        <textarea id="{field.id}" name="{field.id}" placeholder="{field.placeholder}" rows="15"></textarea>
    {/if}
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
        width: 25em;
        display: flex;
        flex-direction: column;
    }
    label {
        margin-bottom: 0.5em;
        font-weight: bold;
        font-size: 1.1em
    }
    input, textarea {
        margin-bottom: 1em;
        padding: 0.5em;
        border-radius: 0.5em;
        font-size: 1.01em;
        border: 0.05em solid black;
    }
    .button-container {
        display: flex;
        justify-content: center;
        margin: 0em 0em 1em 0em;

    }
    button {
        background-color: rgb(42, 190, 42);
        border-style: none;
        color: rgb(223, 223, 223);
        border-radius: 8px;
        padding: 0.8em 5em;
        font-weight: bold;
        font-size: large;
    }
    button:hover {
        background-color: rgb(44, 146, 44);
    }
</style>