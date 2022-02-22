<script>
	export let personData;

	let persons = [];

	// reactive variables!
	// the key to solve your problem
	// read this: https://svelte.dev/tutorial/updating-arrays-and-objects
	// and this:  https://linguinecode.com/post/svelte-reactive-declaration
	// this will trigger each time personData changes

	$: persons = personData ? [...persons, personData] : persons;
	// this ternary operator avoids pushing a null or undefined inside array on first load
	// will only let pass personData if it isn't falsy/nullish

	const handleClick = (id) => {
		console.log(persons);
		persons = persons.filter((people) => {
			return people.id != id;
		});
	};
</script>

<p>Person Data</p>
{#each persons as person}
	<div class="person-box">
		<p>
			<!-- you had "name" here, but it is "firstName"  -->
			<strong>Name: </strong>{person?.firstName}
			<button
				on:click={() => {
					handleClick(person?.id);
				}}>Delete</button
			>
		</p>
		{#if person?.favourites}
			<ul>
				<li><strong>Favs</strong></li>
				{#each person?.favourites as favs}
					<li>{favs}</li>
				{/each}
			</ul>
		{:else}
			<p class="no-favs"><strong><u>No Favs</u></strong></p>
		{/if}
	</div>
{/each}

<style>
	li {
		list-style: none;
	}
	.person-box {
		display: flex;
	}
	.no-favs {
		margin-left: 40px;
	}
</style>
