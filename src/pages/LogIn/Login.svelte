<script>
    import { BASE_URL } from "../../stores/baseURL.js";
    import Form from "../../components/form/Form.svelte";
    import { user } from '../../stores/user.js'
    import { useNavigate, useLocation } from 'svelte-navigator'

    const navigate = useNavigate()
    const location = useLocation()

    /*
    Right now, the user is being set no matter the input. Only set user if authenticated through the backend. Also use JWT
    */

    
    const fields = [
        {
            id: 'username',
            labelText: 'Username',
            placeholder: 'username here...'
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
    endpoint={$BASE_URL + '/api/login'}
    links={links} 
    callback={async data => {
        $user = { username: data.get("username"), password: data.get("password") }
        const from = ($location.state && $location.state.from) || "/"
        navigate(from, { replace: true})
        }}>
</Form>

<style>

</style>