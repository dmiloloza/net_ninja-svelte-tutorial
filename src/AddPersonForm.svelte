<script>
    import {createEventDispatcher} from 'svelte'

    let dispatch = createEventDispatcher()

    let name;
    let beltColor;
    let age;
    let skills = [];

    const handleSubmit = () => {
        const person = {
            name,
            beltColor,
            age,
            skills,
            id: Math.random()
        };
        dispatch('addPerson', person);
    }
</script>

<form on:submit|preventDefault={handleSubmit}>
    <input bind:value={name} placeholder="name" type="text">
    <input bind:value={age} placeholder="age" type="number">
    <label>Skills:</label>
    <input bind:group={skills} type="checkbox" value="fighting">fighting<br>
    <input bind:group={skills} type="checkbox" value="sneaking">sneaking<br>
    <input bind:group={skills} type="checkbox" value="running">running<br>
    <select bind:value={beltColor}>
        <option value="Black">Black</option>
        <option value="Orange">Orange</option>
        <option value="Brown">Brown</option>
        <option value="White">White</option>
    </select>
    <button>Add Person</button>
</form>

<style>
</style>