<script>
  import { onMount } from "svelte";
  import MsgForm from "./MsgForm.svelte";
  import MsgList from "./MsgList.svelte";

  import { testWebSocket } from "./ws";
  let websocket;
  const sendMessage = ({ detail }) => {
    websocket.send(detail.text);
  };
  const messages = [];

  onMount(() => {
    testWebSocket();
  });
</script>

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

<main>
  <h1>Svelte Chat!</h1>
  <MsgList {messages} />
  <MsgForm on:send={sendMessage} />
</main>
