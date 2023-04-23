<script>
    import { BASE_URL } from "../../store/baseURL";
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
            placeholder: 'password here...',
            type: 'password'
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

<h1>Log in</h1>

<Form 
    fields={fields} 
    submitBtnText="Log In" 
    endpoint={$BASE_URL + '/log-in'}
    links={links} 
    callback={async response => {
        alert('hit the callback')
        return response
        
        
}}></Form>

<style>

</style>