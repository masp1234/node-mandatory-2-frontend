
<script>
    import { BASE_URL } from "../../stores/baseURL.js";
    import Form from "../../components/form/Form.svelte";

    const fields = [
        {
            id: 'email',
            labelText: 'Email',
            placeholder: 'email here...',
        },
        {
            id: 'subject',
            labelText: 'Subject',
            placeholder: 'subject here...',
        }
        ,
        {
            id: 'message',
            labelText: 'Message',
            placeholder: 'type your message to us here...',
            tag: 'textarea'
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

<h1>Contact</h1>

<Form
    fields={fields}
    endpoint={$BASE_URL + '/api/mail?type=contact'}
    links={links}
    >
</Form>

<style>

</style>