<template>
    <div class="addtask">
        <input type="text" class="inputTask" placeholder="Task">
        <div class="important">    
            <button v-on:click="focus(1)" class="btn1"></button>
            <button  v-on:click="focus(2)" class="btn2"></button>
            <button  v-on:click="focus(3)" class="btn3"></button>
            <button  v-on:click="focus(4)" class="btn4"></button>
            <button  v-on:click="focus(5)" class="btn5"></button>
        </div>
        <button v-on:click="AddTask()" class="addbtn"> Добавить</button>
    </div>
</template>


<style scoped>
    @import 'addtask.css';
</style>

<script>
export default {
    methods: {
        focus: function (id){
            console.log(id);
            document.querySelector('.btn1').className = 'btn1'
            document.querySelector('.btn2').className = 'btn2'
            document.querySelector('.btn3').className = 'btn3'
            document.querySelector('.btn4').className = 'btn4'
            document.querySelector('.btn5').className = 'btn5'
            document.querySelector('.btn'+id).className += ' focused'
        },
        AddTask: async function(){
            //console.log(document.querySelector('.inputTask').value)
            if (document.querySelector('.inputTask').value == ''){
                alert("Заполните Input");
                return 0;
            }else{
                const input = document.querySelector('.inputTask').value;
                const btn = document.querySelector('.focused').className[3];
                const data = {
                    "name" : input,
                    "important" : btn
                };
                const url = 'http://127.0.0.1:5000/addtask';
                const response = await  fetch(url, {
                    method : 'POST',
                    body : JSON.stringify(data),
                    headers : {
                        'Content-Type' : 'application/json'
                    }
                });
                const json = await response.json();
                location.reload()
                alert(json);
            }
        }
    }
}
</script>