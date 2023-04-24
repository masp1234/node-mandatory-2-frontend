<script>
    import { BASE_URL } from "../../stores/baseURL";
    import Form from "../../components/form/Form.svelte";

    const fields = [
        {
            id: 'username',
            labelText: 'Username',
            placeholder: 'username here...'
        },
        {
            id: 'password',
            labelText: 'Password',
            placeholder: 'password here...',
            type: 'password'

        },
        {
            id: 'repeatPassword',
            labelText: 'Repeat password',
            placeholder: 'repeat password here...',
            type: 'password'
        }
    ]
    const links = [
        {
            url: '/log-in',
            text: "Already have an account? Log in here"
        },
    ]
</script>


<h1>Sign up</h1>

<Form
    fields={fields}
    links={links}
    endpoint={$BASE_URL + '/api/users'}
    submitBtnText={'Sign Up'}
    callback={async response => {
        alert('hit the endpoint')
        console.log(response.status)
    }}></Form>