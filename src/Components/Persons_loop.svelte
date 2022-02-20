<script>
import { onMount } from "svelte";


    export let personData;
    console.log(personData)
    let persons = [
        {
            name: "sa",
            location: "isl",
            age: 29,
            favourites: ["cooking", "reading", "working"],
            id: 1
        },
        { name: "uz", location: "isl", age: 29, id: 2 },
        { name: "wa", location: "isl", age: 29, id: 3 },
    ];
    const handleClick = (id) => {
        console.log(id)
        persons = persons.filter((people) => {
            return people.id != id;
        })
    }
    // persons.push(personData)
</script>
<style>
    li{
        list-style: none;
    }
    .person-box{
        display: flex;
    }
    .no-favs{
        margin-left: 40px;
    }
</style>

<p>Person Data</p>
{#each persons as person}
    <div class="person-box">
        <p><strong>Name: </strong>{person.name} <button on:click={() => {handleClick(person.id)}}>Delete</button> </p>
        {#if person.favourites}
            <ul>
                <li><strong>Favs</strong></li>
                {#each person.favourites as favs}
                     <li>{favs}</li>
                {/each}
            </ul>
        {:else}
            <p class="no-favs"><strong><u>No Favs</u></strong></p>
        {/if}

    </div>
{/each}
