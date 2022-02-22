<script>
	import Form from "./Components/Form.svelte";
	import Modal from "./Components/Modal.svelte";
	import PersonsLoop from "./Components/Persons_loop.svelte";
	import Header from "./Components/Header.svelte";
	// export let name;
	let openModal = false;
	let person

	const toggleModal = () => {
		openModal = !openModal;
	};
	const addPersonCustomEvent = (e) => {
		person = e.detail;
		console.log(person);
	};
</script>

<main>
	<Header />
	<button
		on:click={() => {
			toggleModal();
		}}>open modal</button
	>
	<section>
		<!--  i think you dont need to bind: here -->
		<PersonsLoop personData={person} />
	</section>
</main>
<Modal
	isPromo={true}
	body="main modal here"
	{openModal}
	on:click={() => {
		toggleModal();
	}}
>
	<!-- You were missing the event parameter here -->
	<Form on:addPerson={(event) => addPersonCustomEvent(event)} />
</Modal>
