<script>
    import Form from "../../components/form/Form.svelte";
    const fields = [
        {
            id: 'email',
            labelText: 'Email',
            placeholder: 'email here...'

        }
        ,
        {
            id: 'password',
            labelText: 'Password',
            placeholder: 'password here...'

        },
    ]
</script>

<Form fields={fields} actionEndpoint={'/login'}></Form>

<style>

</style>