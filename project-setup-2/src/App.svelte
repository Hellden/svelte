<script>
  import ContactCard from "./ContactCard.svelte";

  let name = "Max";
  let title = "";
  let image = "";
  let description = "";
  let formState = "empty";
  let createdContacts = [];

  let password = "";

  function addContact() {
    if (
      name.trim().lenght == 0 ||
      title.trim().length == 0 ||
      image.trim().length == 0 ||
      description.trim().length == 0
    ) {
      formState = "invalid";
      return;
    }
    createdContacts = [
      ...createdContacts,
      {
        name: name,
        jobTitle: title,
        imageUrl: image,
        desc: description
      }
    ];
    formState = "done";
  }
</script>

<style>
  #form {
    width: 30rem;
    max-width: 100%;
  }
</style>

<div id="form">
  <div class="form-control">
    <label for="userName">User Name</label>
    <input type="text" bind:value={name} id="userName" />
  </div>
  <div class="form-control">
    <label for="jobTitle">Job Title</label>
    <input type="text" bind:value={title} id="jobTitle" />
  </div>
  <div class="form-control">
    <label for="image">Image URL</label>
    <input type="text" bind:value={image} id="image" />
  </div>
  <div class="form-control">
    <label for="desc">Description</label>
    <textarea rows="3" bind:value={description} id="desc" />
  </div>
</div>

<button on:click={addContact}>Add Contact Card</button>

{#if formState === 'invalid'}
  <p>Invalid input.</p>
{:else}
  <p>Please enter some data and hit the button !</p>
{/if}

{#each createdContacts as contact, id (contact.id)}
  <h2>#{id}</h2>
  <ContactCard
    userName={contact.name}
    jobTitle={contact.jobTitle}
    description={contact.desc}
    userImage={contact.imageUrl} />
{/each}

<h1>Exercice practice</h1>

<label for="s">Password</label>
<input type="password" bind:value={password} />
{password.length}
{#if password.length <= 5}
  <h2>Too short is dangerous</h2>
{:else if password.length >= 10}
  <h2>The password is too long</h2>
{:else}
  <h2>The password is ok !</h2>
{/if}
