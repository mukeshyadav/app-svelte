<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();
  let text = "";
  let disableFormSending = true;
  // reactive statement
  $: disableFormSending = text.length > 5;

  const sendMessage = () => {
    dispatch("send", {
      text
    });
  };
</script>

<input bind:value={text} />
<button on:click={sendMessage} disabled={!disableFormSending}>Send</button>
