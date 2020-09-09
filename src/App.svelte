<script>
    let firstName = 'John';
    let lastName = 'Doe';
    let beltColor = 'black';

    let people = [
        {
            name: 'Yoshi',
            beltColor: 'yellow',
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
        },{
            name: 'Bowser',
            beltColor: 'black',
            age: 37,
            id: 8
        }

    ]

    $: fullName = `${firstName} ${lastName}`;
    $: console.log(beltColor);

    const handleClick = id => {
        //delete the person from people. False filters that item from array (person.id !== id)
        people = people.filter(person => person.id !== id)
    };
    console.log(people.length)
</script>

<main>
    <p>{fullName} - {beltColor} belt</p>
    <input bind:value={firstName} type="text">
    <input bind:value={lastName} type="text">
    <input bind:value={beltColor} type="text">
    <hr>
    {#if people.length === 1 }
        <p>Solo ninja</p>
    {:else if people.length <=3}
        <p>Small team</p>
    {:else}
        <p>Ninja squad</p>
    {/if}
    <hr>
    <div>
        {#each people as person (person.id)}
            <div>
                <h4>{person.name}</h4>
                {#if person.beltColor === 'black'}
                    <p><strong>MASTER NINJA</strong></p>
                {/if}
                <p>{person.age} years old, {person.beltColor} belt</p>
                <button on:click={() => handleClick(person.id)}>delete</button>
            </div>
        {:else}
            <p>There are no people to show!</p>
        {/each}
    </div>
    <hr>


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