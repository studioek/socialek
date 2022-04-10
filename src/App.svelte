<script>
	import {
		Router,
		Route,
		Link
	} from "svelte-navigator";
	import Login from "./components/Login/Login.svelte";
	import PrivateRoute from "$/components/Private/PrivateRoute.svelte";
	import {
		user
	} from "$/stores";

	function handleLogout() {
		$user = null;
	}
</script>

<main>
	<Router>
		<header>
			<h1>History</h1>

			<nav>
				<Link to="/">Home</Link>
				<Link to="about">About</Link>
				<Link to="profile">Profile</Link>
			</nav>
		</header>

		<main>
			<Route path="login">
				<Login />
			</Route>

			<Route path="/">
				<h3>Home</h3>
				<p>Home sweet home...</p>
			</Route>

			<Route path="about">
				<h3>About</h3>
				<p>That's what it's all about!</p>
			</Route>

			<PrivateRoute path="profile" let:location>
				<h3>Welcome {$user.username}</h3>
				<button on:click={handleLogout}>Logout</button>
			</PrivateRoute>
		</main>
	</Router>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>