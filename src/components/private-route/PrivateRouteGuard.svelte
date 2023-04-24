<script>
    import { useNavigate, useLocation} from 'svelte-navigator'
    import { user } from '../../stores/user.js'

    const navigate = useNavigate();
    const location = useLocation();

    $: if (!$user) {
        navigate("/log-in", {
            state: { from: $location.pathname },
            replace: true,
        });
    }
</script>

{#if $user}
    <slot></slot>
{/if}