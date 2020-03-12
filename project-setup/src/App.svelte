<script>
  let course = "";
</script>

<style>
  .current {
    color: red;
  }

  #form {
    width: 30rem;
    max-width: 100%;
  }
</style>

<h1>Practice exercice</h1>

<label for="">Couses goal</label>
<input type="text" bind:value={course} />

<h1 class:current={!course == ''}>{course}</h1>
