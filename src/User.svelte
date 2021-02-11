<script lang="ts">
    import Processes from "./Processes.svelte";
    import {currentUsers} from "./stores";

    export let user;

    let activeUsers  = 1;
    let userProcesses = 0;
    let avaiableResource = 0;

    const unsubscribe = currentUsers.subscribe((_users) => {
        const usersProcesses = Object.values(_users)
        const activeUsersProcesses = usersProcesses.filter((_users) => {
           return _users > 0
        } )
        activeUsers  = activeUsersProcesses.length || 1 ;

        userProcesses = _users[user.id];

        avaiableResource = userProcesses > 0 ? (100/activeUsers) : 0;
    })

</script>

<main>
    <div class="user"  >
        <p>{user.name}</p>
        <p> {avaiableResource.toFixed(2)}</p>
        <slot>
            <Processes  {user} {activeUsers}/>
        </slot>

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


    div.user {
        background-color: white;
        min-width: 530px;
        min-height: 530px;

        box-shadow: 1px black;
        margin-right: 16px;
    }

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>