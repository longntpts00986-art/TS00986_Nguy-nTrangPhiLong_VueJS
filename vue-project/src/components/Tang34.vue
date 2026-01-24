<template>
    <div>
        <!--   <h1>Hien thi noi dung o day</h1> -->
        <h6 v-html="content" v-bind:style="styleData" v-bind:class="className"></h6>
        <h2>{{ message }}</h2>
        <h2 v-html="number + 5"></h2>
        <h4>{{ sayHi() }}</h4>
        <button @click="changeMessage()">changeMessage</button>
        <button @click="changeContent()">changeContent</button>
        
    </div>
</template>
<script>
    export default {
        data() {
            return{
                content: 'Xin chao cac ban',
                message: 'Xin chao VueJS',
                number: 10,
                className: 'text-red',
                styleData: 'font-size: 5rem'
            
            }
        },
        methods: {
            sayHi() {
                return ' Day la mot phuong thuc'
            },
            changeMessage() {
                this.message = 'day la noi dung moi'
            },
            changeContent(){
                this.content = 'Da doi thanh cong noi dung moi'
                this.className = 'text-blue'
            }
        }
    }
</script>
<style>
    .text-blue{
        color:blue;
    }    
</style>