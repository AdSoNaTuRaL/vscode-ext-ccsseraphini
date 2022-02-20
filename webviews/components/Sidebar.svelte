<script lang="ts">
  import { suffix, maxTweetLength } from "../../src/constants";
  let text = "";
</script>

<div style="display: flex;">
  <img
    src="https://pbs.twimg.com/profile_images/1494329046678659072/RprvW5s4_400x400.jpg"
    alt="Seraphini Icon"
    style="max-width: 100px; border-radius: 100px; padding: 8px; margin: auto;"
  />
</div>

<form
  on:submit|preventDefault={() => {
    text = "";
  }}
>
  <textarea
    bind:value={text}
    id="tweet"
    rows="10"
    placeholder="Write your tweet concept/question here"
  />

  <p class:exceeded={text.length + suffix.length > maxTweetLength}>
    Typed characters: {text.length}
  </p>
  <p>Maximum characters: {maxTweetLength}</p>

  <!-- svelte-ignore missing-declaration -->
  <button
    style="margin-top: 16px;"
    on:click={() => {
      const tweet = encodeURIComponent(`${text}${suffix}`);

      if (tweet.length > maxTweetLength) {
        tsvscode.postMessage({
          type: "onError",
          value: "Your tweet exceeded the maximum of characters allowed!",
        });
        return;
      }

      tsvscode.postMessage({ type: "onInfo", value: tweet });
    }}>Tweet</button
  >
</form>

<style>
  .exceeded {
    color: red;
  }
</style>
