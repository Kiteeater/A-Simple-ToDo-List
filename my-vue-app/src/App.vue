<script setup>
import { ref } from 'vue';
  
  const Things = ref('') ;
  const UserName = ref('');
  const list = ref([
    {
        Done: false,
        text:'吃饭',
    },
    {
        Done: false,
        text:'睡觉',
    },
  ])
  function add(){
    list.value.push({
        Done:false,
        text:Things.value,
    })
    Things.value = '';
  }
  function Done(index){
    list.value[index].Done = !list.value[index].Done; 
  }
  function DEL(index){
    list.value.splice(index,1)

  }


</script>
<template>
    <div>
        <div class="TOP"> TODO LIST </div>
        <div class="InputForm">
            <input v-model = "Things"class ="AddSomething" type="text" placeholder="Add Your Plan!!!"/>
            <div @click = "add" class="TheButton">PUSH</div>
        </div>
        <div v-for="(item,index) in list" class="item">
            <input v-model="item.Done"  type="checkbox" >
            <div :class="[item.Done ? 'isDone': 'Name']">{{ item.text }}</div>
            <div @click = "DEL(index)"class="DEL">dle</div>
        </div>
    </div>
</template>

<style scoped>
        .Name{
            height: 34px;
            width: 90%;
            font-size: 25px;
            margin: 0;
            padding: 0;
            line-height: 34px;
            position:relative;
            text-align: left;
        }
        .DEL{
            height: 100%;
            width: 5%;
            color: white;
            font-size: 15px;
            line-height: 34px;
            padding-left: 5px;
            background-color: #df7171;
            cursor: pointer;
            margin: 0;
            border-radius: 0 20px 20px 0;
            text-align: center;
        }
        .isDone{
            height: 34px;
            width: 90%;
            font-size: 25px;
            margin: 0;
            padding: 0;
            line-height: 34px;
            position:relative;
            text-align: left;
            color: gray;
            text-decoration: line-through;

        }
        .item{
            display: flex;
            align-items: center;
            justify-content: space-between;
            width: 80%;
            height:40px;
            margin: 8px;
            margin-top: 20px;
            margin-left: 10%;
            padding:0 0 0 8px;
            border-color: #4768ed;
            border-radius: 20px;
            box-shadow: #525252 0px 4px 15px;
        }

        .AddSomething::placeholder {
             position: relative;
             left: 10px; /* 仅调整 placeholder 的水平偏移 */
             color: rgb(151, 149, 149);
         }
        .TheButton{
            height: 44px;
            width:80px;
            background: linear-gradient(to right,rgb(117, 207, 165),rgb(59, 59, 225));
            text-align: center;
            border-radius: 0 10px 10px 0;
            color:#ffff;
            line-height: 44px;
            cursor: pointer;
            box-sizing: border-box; 
            margin: 0;
            padding: 0;
        }
        .AddSomething{
            border-radius:10px 0 0 10px;
            outline: none;
            padding: 0 10px; 
            width: 60%;
            height: 40px;
        }
        .InputForm{
            display: flex;
            justify-content: center;
            height: 100px;
        }
        .TOP{
            font-size: 30px;
            color: #2b0c51;;
            text-align: center;
            margin-top: 20px;
            width:100%;
            height:50px;

        }
        body{
            background: linear-gradient(to left,rgb(117, 207, 165),rgb(59, 59, 225));
            display:flex;
            justify-content: center; /* 水平居中 */
        }
        div{
            background-color:#ffff;
            width:96%;
            height:800px;
            border-radius: 10px;
            margin-top: 5px;
            overflow: hidden;
            margin-left: 2%;
        
        }
</style>
