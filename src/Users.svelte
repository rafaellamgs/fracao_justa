<script lang="ts">

    import {currentUsers} from "./stores";
    import User from "./User.svelte";

    let users = [{name: 'user1', id: 'user1'}];

    function addUser() {
        const usersLength = users.length  + 1;
        users.push({
            name: `user${usersLength}`,
            id: `user${usersLength}`,
        })

        users = users;

        currentUsers.update((_users) => {
            _users[`user${usersLength}`] = 0
            return _users
        })


    }
</script>

<main>
    <button on:click="{addUser}">Criar Usuário</button>
    <div class="wrapper">

        {#each users as user}
            <User {user} />
        {/each}
    </div>

</main>














<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 530px;
		margin: 0 auto;
        background-color: blanchedalmond;
	}

    div.wrapper {
        display: grid;
        grid-gap: 10px;
        grid-template-columns: repeat(auto-fill, 530px);
    }

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>