<script>
    import {
        useNavigate,
        useLocation
    } from 'svelte-navigator';
    import {
        user
    } from "$/stores";

    const navigate = useNavigate();
    const location = useLocation();

    let username;
    let password;


    function handleSubmit() {
        $user = {
            username,
            password
        };
        const from = ($location.state && $location.state.from) || '/';
        navigate(from, {
            replace: true
        });
    }
</script>

<h3>
    Login
</h3>
<form on:submit={handleSubmit}>
    <input type="text" name="username" bind:value={username} />
    <br />
    <input type="password" name="password" bind:value={password} />
    <br />
    <button type="submit">Login</button>
</form>