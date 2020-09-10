<script>
    let name;
    let beltColor;
    let age;

   const handleSubmit = () => console.log(name)
</script>

<form on:submit|preventDefault={handleSubmit}>
    <input bind:value={name} placeholder="name" type="text">
    <input bind:value={beltColor} placeholder="belt color" type="text">
    <input bind:value={age} placeholder="age" type="number">
    <button>Add Person</button>
</form>

<style>
</style>