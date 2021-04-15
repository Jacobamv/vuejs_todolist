<template>
    <div class="tasks">
            <table class="table">
                <thead class="thead-dark">
                    <tr>
                    <th scope="col">#</th>
                    <th scope="col">Название</th>
                    <th scope="col">Важность</th>
                    <th scope="col">Выполнить</th>
                    <th scope="col">Удалить</th>

                    </tr>
                </thead>
                <tbody>
                    <tr v-for="task in data" :key="task.id">
                    <th scope="row">{{task.id}}</th>
                    <td>{{task.name}}</td>
                    <td v-if="task.important == 1">
                        <div class="btn1"></div>
                    </td>
                    <td v-if="task.important == 2">
                        <button class="btn2"></button>
                    </td>
                    <td v-if="task.important == 3">
                        <button class="btn3"></button>
                    </td>
                    <td v-if="task.important == 4">
                        <button class="btn4"></button>
                    </td>
                    <td v-if="task.important == 5">
                        <button class="btn5"></button>
                    </td>

                    <td v-if="task.done == true">
                        <button class="btn"  v-on:click="toDo(task.id)" >DONE</button>
                    </td>
                    <td v-if="task.done == false">
                        <button class="btn" v-on:click="toDo(task.id)">Not</button>
                    </td>
                    <td>
                        <button class="btn" v-on:click="delete_task(task.id)">X</button>
                        </td>
                    </tr>

                </tbody>
                </table>
    </div>
</template>


<style scoped>
    @import 'tasks.css';
    @import 'https://stackpath.bootstrapcdn.com/bootstrap/4.4.1/css/bootstrap.min.css';
</style>


<script>
export default {
    data (){
        return {
            data : {}
        }
    },
    beforeMount(){
        this.getName();
    },
    methods: {
        async getName(){
            const res = await fetch('http://127.0.0.1:5000/gettasks', );
            const data = await res.json();
            console.log(data);
            this.data = data;
        },
        toDo : async function (id){
            const res = await fetch('http://127.0.0.1:5000/do/' + id);
            const response = await res.json();
            alert(response);
            location.reload();
        },
        delete_task: async function(id){
                const url = 'http://127.0.0.1:5000/delete/' + id;
                const response = await  fetch(url, {
                    method : 'DELETE',
                });
                const json = await response.json();
                alert(json);
                location.reload()
        }
    }
};
</script>