<script>
    let tasks = [];
    let nameTask = '';

    function addTask(event){
        if(event.key === 'Enter'){

            const task = {
                name: nameTask,
                state: false
            }
            tasks.push(task);
            console.log(tasks);
            tasks = tasks;
            nameTask = '';
        }
    }

    function deleteTask(i){
        tasks.splice(i, 1);
        tasks = tasks;
    }

    function updateTask(task, i){
        task[i].state = !task.state
    }
</script>

<div>
    <div class="container mt-5">
        <div class="row">
            <div class="col-lg-8 offset-lg-2">
                <input type="text" class="form-control form-control-lg"
                    on:keydown={addTask}
                    bind:value={nameTask}    
                    placeholder="Enter task..">
            <br>
            </div>

,           <div class="col-lg-6 offset-lg-3">
                {#if tasks.length === 0}
                <div class="card p-2">
                    <h6>No task to show</h6>
                </div>
                {/if}

                <ul class="list-group">
                {#each tasks as task, i}
                <li class="list-group-item d-flex justify-content-between">
                    <span class={task.state === true ? 'text-success cursor' : 'cursor'} on:click={() => updateTask(task, i)}>
                        <i class={task.state === true ? 'fas fa-check-circle' : 'far fa-circle'} ></i>
                    </span>
                        <h5>{ task.name }</h5>
                        <span class="cursor text-danger" on:click={() => deleteTask(i)}>
                            <i class="fas fa-trash-alt"></i>
                        </span>
                </li>
                {/each}
                </ul>
            </div>
        </div>
    </div>
</div>

<style>
    .form-control-lg {
        font-size: 1.8rem;
    }
    input {
        text-align: center;
    }

    .cursor {
        cursor: pointer;
    }
</style>