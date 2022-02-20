<script>
    import { createEventDispatcher } from "svelte";
    let dispatch = createEventDispatcher();
    let firstName;
    let location;
    let age;

    const handleForm = () => {
        let formValues = {
            firstName,
            location,
            age,
            id: Math.random(),
        };
        dispatch("addPerson", formValues);
    };
</script>

<!-- markup (zero or more items) goes here -->

<form on:submit|preventDefault={handleForm}>
    <input type="text" bind:value={firstName} />
    <input type="text" bind:value={location} />
    <input type="number" name="" id="" bind:value={age} />
    <input type="submit" value="submit" />
</form>

<style>
    /* your styles go here */
    form {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
    }
</style>
