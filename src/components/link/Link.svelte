<script>
    export let url
    export let text = 'Click here'
</script>

<a href={url}>{text}</a>

<style>
    a {
        text-decoration: none;
        color: goldenrod;
    }
    a:hover {
        color: goldenrod;
        scale: 1.05;
    }
</style>