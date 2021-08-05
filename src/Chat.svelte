<script lang="ts">
  import {WebsocketBuilder} from "websocket-ts";
  let client_id = Date.now();
  let ws = new WebsocketBuilder(`ws://localhost:8000/play/foo/in/${client_id}`).onMessage(
    (instance, event) => {
      messages = [...messages, event.data];
    }
  ).build();
  let messages = [];
  let messageToSend = '';
  function sendMessage() {
    ws.send(messageToSend)
    messageToSend = ''
  }
</script>

<p>Hello world</p>
<h1>WebSocket Chat</h1>
<h2>Your ID: {client_id}</h2>
<input type="text" autocomplete="off" bind:value="{messageToSend}"/>
<button on:click="{sendMessage}">Send</button>
<ul id='messages'>
  {#each messages as message}
    <li>{message}</li>
  {/each}
</ul>
