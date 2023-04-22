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
    const links = [
        {
            url: '/sign-up',
            text: "Don't have an account yet? Sign up here"
        },
        {
            url: '/forgot-password',
            text: 'Forgot your password? Click here'
        }
    ]
</script>

<Form fields={fields} submitBtnText="Log In" actionEndpoint={'http://localhost:8080/log-in'} links={links}></Form>

<style>

</style>