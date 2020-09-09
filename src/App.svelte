<script>
    let people = [
       /* {
            name: 'Yoshi',
            beltColor: 'black',
            age: 25,
            id: 1
        }, {
            name: 'Mario',
            beltColor: 'orange',
            age: 45,
            id: 2
        }, {
            name: 'Luigi',
            beltColor: 'brown',
            age: 35,
            id: 3
        }*/
    ]

    let firstName = 'John';
    let lastName = 'Doe';
    let beltColor = 'black';

    $: fullName = `${firstName} ${lastName}`;
    $: console.log(beltColor)
</script>

<main>
    <p>{fullName} - {beltColor} belt</p>
    <input bind:value={firstName} type="text">
    <input bind:value={lastName} type="text">
    <input bind:value={beltColor} type="text">
    <div>
        {#each people as person (person.id)}
            <div>
                <h4>{person.name}</h4>
                <p>{person.age} years old, {person.beltColor} belt</p>
            </div>
            {:else}
            <p>There are no people to show!</p>
        {/each}
    </div>
</main>

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