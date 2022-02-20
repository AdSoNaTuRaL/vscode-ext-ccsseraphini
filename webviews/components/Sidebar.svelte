<script lang="ts">
  let tweet = "";
</script>

<!-- FIX ALIGN -->
<div align="center">
  <img 
    src="https://pbs.twimg.com/profile_images/1494329046678659072/RprvW5s4_400x400.jpg" 
    alt="Seraphini Icon" 
    style="max-width: 100px; border-radius: 100px; padding: 8px;"
  />
</div>

<form>
  <textarea 
    bind:value={tweet} 
    id="tweet" 
    rows="10" 
    placeholder="Write your tweet concept/question here" 
    on:input={() => {
      // TODO: Add Validation to Character limit 264
    }} 
  />

  <p>Typed characters: {tweet.length}</p>
  <p>Maximum characters: 264</p>
  
  
  <button style="margin-top: 16px;" on:click={() => {
    // Add Validation before send to twitter a
    console.log('send to twitter API');
    tweet = "";
  }}>Tweet</button>
</form>

<pre>{JSON.stringify(tweet, null, 2)}</pre>
