<script>
    import { BASE_URL } from "../../stores/baseURL";
    import { onMount } from "svelte";
    let users;
    let errorMessage;

    onMount(async() => {
        const response = await fetch($BASE_URL + '/api/users')
        console.log(response)
        if (response.status !== 200) {
            errorMessage = 'You are not authorized to view this content';
            return
        }
        users = await response.json();
        console.log(users)
    });
</script>
{#if errorMessage}
<h1>{errorMessage}</h1>
{/if}
{#if users}
<p>{users}</p>
{/if}
