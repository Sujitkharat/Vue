<template>

    <div class="full">
        <main>
            <span v-if="this.ready">{{value}}</span>
        <h1>{{heading}}</h1>
        <button v-show="ready" v-on:click="low_clicked()"  class="btn">TOO LOW</button>
        <button v-on:click="ready_clicked()" class = "btn">{{bname}}</button>
        <button v-show="ready" v-on:click="high_clicked()" class = "btn">TOO HIGH</button>
        <button v-show="ready" v-on:click="resart()" class = "res_btn">RESTART</button>
        
        </main>
    </div>
</template>

<script>
export default {
    name:'Home',
   data(){
       return{
           low:0,
           high:100,
           ready:false,
           value:Math.round(Math.random()*100),
           bname:"READY",
           heading:"Guess a random number between 1-100"
       }
   },
    methods:{
        low_clicked(){
            // console.log("Low clicked");
            this.low = this.value;
            this.value = Math.round((this.low + this.high)/2);
        },
        ready_clicked(){

            if(this.bname==="CORRECT"){
                this.$swal({  
                type: 'success',  
                title: 'We caught your guess !!'
            }); 

                
            }
            this.ready = true;
            this.heading = ""
            this.bname = "CORRECT";
        },
        high_clicked(){
            // console.log("You have clicked HIGH");
            this.high = this.value;
            this.value = Math.round((this.low + this.high)/2);
        },
        resart(){
            window.location.reload()
        }

    }
}
</script>

<style>

.full {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 95vh;
}

main {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: 100px 50px;
    grid-gap: 10px;
}

h1 {
    grid-column: 1/-1;
    font-size: 34px;
    color: rgb(37, 0, 0)
}

.btn {
    font-size: 23px;
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    background-color: rgb(13, 33, 100);
    color: rgb(255, 255, 255);
    border-radius: 12px;
    cursor: pointer;
}

span {
    position: absolute;
    font-size: 190px;
    left: 42%;
    top: 12%;
    color: rgb(20, 5, 5);
    font-weight: bold;
}

.res_btn {
    height: 50px;
    font-size: 23px;
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    background-color: rgb(13, 33, 100);
    color: rgb(255, 255, 255);
    border-radius: 12px;
    cursor: pointer;
    position: absolute;
    bottom: 20%;
    left: 46%;
}

.btn:hover,
.res_btn:hover {
    background-color: rgb(253, 219, 219);
    color: rgb(0, 0, 0);
}

</style>