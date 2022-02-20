<script lang="ts">
  const suffix = '\ncc @sseraphini';
  let text = "";
</script>

<!-- FIX ALIGN -->
<div align="center">
  <img 
    src="https://pbs.twimg.com/profile_images/1494329046678659072/RprvW5s4_400x400.jpg" 
    alt="Seraphini Icon" 
    style="max-width: 100px; border-radius: 100px; padding: 8px;"
  />
</div>

<form on:submit|preventDefault={() => {
    text = "";
    console.log('send to twitter API');
}}>
  <textarea 
    bind:value={text} 
    id="tweet" 
    rows="10" 
    placeholder="Write your tweet concept/question here" 
    on:input={() => {
      // TODO: Add Validation to Character limit 264
    }} 
  />

  <p>Typed characters: {text.length}</p>
  <p>Maximum characters: 264</p>
  
  
  <button style="margin-top: 16px;" on:click={() => {
    // Add Validation before send to twitter a
    const tweet = encodeURIComponent(`${text}${suffix}`);
    tsvscode.postMessage({ type: 'onInfo', value: tweet });
  }}>Tweet</button>
</form>