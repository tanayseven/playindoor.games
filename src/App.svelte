<script lang="ts">
	import SimplePeer from 'simple-peer'
	import { WebsocketBuilder } from 'websocket-ts'
	import { Router, Link, Route } from "svelte-routing"
	import Home from "./home"
	import TicTacToe from "./tic-tac-toe"
	import Roshambo from "./roshambo"
	import Chat from './Chat.svelte'
	export let url = "";
</script>

<Router url="{url}">
	<nav>
		<Link to="/">Home</Link>
		<Link to="/tic-tac-toe">TicTacToe</Link>
		<Link to="/roshambo">Roshambo</Link>
		<Link to="/chat">Chat</Link>
	</nav>
	<div>
		<Route path="/tic-tac-toe" component="{TicTacToe}" />
		<Route path="/roshambo" component="{Roshambo}" />
		<Route path="/chat" component="{Chat}" />
		<Route path="/"><Home /></Route>
	</div>
</Router>

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
