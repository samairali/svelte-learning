<script>
	import Form from './Form.svelte';
    // your script goes here
    export let body;
    export let openModal;
    export let isPromo = false;
</script>

{#if openModal}
    <div class="modal" on:click|self class:promo={isPromo} >
        <div class="modal-body">
            <p>{body}</p>
            <slot></slot>
        </div>
    </div>
{/if}

<style>
    .modal{
        background-color: rgba(0, 0, 0, 0.8);
        position: fixed;
        width: 100%;
        height: 100%;
        top: 0;
        left: 0;
    }
    .modal-body{
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        color: #000;
        /* padding: 50px; */
        background-color: #fff;
        width: 90%;

    }
    .modal-body p{
        padding: 10px;
        text-align: center;
    }
</style>