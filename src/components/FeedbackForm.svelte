<script>
  import {v4 as uuidv4} from 'uuid'
  import {createEventDispatcher} from 'svelte'
  import Card from './Card.svelte'
  import Button from './Button.svelte'
  import RatingSelect from './RatingSelect.svelte';

  const dispatch = createEventDispatcher()
  let text = ''
  let btnDisabled = true
  let min = 1
  let message 
  let rating = 10


  function handleInput(event) {
    text = event.target.value;

    if (text.trim().length < min) {
      message = `Text must be at least ${min} characters`;
      btnDisabled = true;
    } else {
      message = null;
      btnDisabled = false;
    }
  }

  const handleSelect = e => rating = e.detail

  function handleSubmit() {
    if (text.trim().length >= min) {
      const newFeedback = {
        id: uuidv4(),
        text,
        rating: +rating
      };

       dispatch('add-feedback', newFeedback);

       text = ''; // reset the input
       btnDisabled = true;
      
    }
  }
</script>


<Card>
<header>
    <h2>How would you rate your service with us?</h2>
</header>

<form on:submit|preventDefault = {handleSubmit}>
 <RatingSelect on:rating-select={handleSelect}/>
 <div class="input-group">
    <input type="text" on:input={handleInput} bind:value= {text} placeholder="Tell us something that keeps you coming back">
     <Button disabled={btnDisabled} type="submit">Send</Button>
</div>
{#if message}
    <div class="message">
        {message}
    </div>
{/if}

</form>
</Card>


<style>
  header {
    max-width: 400px;
    margin: auto;
  }

  header h2 {
    font-size: 22px;
    font-weight: 600;
    text-align: center;
  }

  .input-group {
    display: flex;
    flex-direction: row;
    border: 1px solid #ccc;
    padding: 8px 10px;
    border-radius: 8px;
    margin-top: 15px;
  }

  input {
    flex-grow: 2;
    border: none;
    font-size: 16px;
  }

  input:focus {
    outline: none;
  }

  /* .message{
    padding-top: 10px;
    text-align: center;
    color: rebeccapurple;
  } */
</style>