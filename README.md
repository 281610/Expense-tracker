# Expense-tracker
You can add you expenses
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        body{
            background-color: rgb(32, 31, 31);
        }
        h1{
            text-align: center;
            font-size: xx-large;
            font-weight: bolder;
        }
        .baap{
            height: 100%;
            width: 500px;
            border: 5px solid rgb(146, 0, 0);
            border-radius: 10px;
            margin-left: 500px;
            background-color: gray;
            padding: 20px;
        }
        #des{
            height: 30px;
            width: 500px;
            border: 2px solid black;
            font-size: larger;
        }
        #des:hover{
            border-color: red;
        }
        #select{
            height: 30px;
            width: 500px;
            border: 2px solid black;
            font-size: large;
            text-align: center;
        }
        #amount{
            height: 30px;
            width: 500px;
            border: 2px solid black;
            font-size: large;
        
        }
        #submit{
            height: 30px;
            width: 500px;
            border: 2px solid black;
            border-radius: 20px;
            font-size: large;
            background-color: black;
            color: aliceblue; 
        }
        #submit:hover{
            background-color: blue;
            font-size: x-large;
            
        }
        #table{
            width: 500px;
            border: 2px solid rgb(255, 255, 255);
            font-size: large;
            background-color: rgb(46, 46, 46);
            color: aliceblue;
        }
        .mess{
            color: rgb(255, 0, 0);
            height: 30px;
            width: 500px;
            text-align: center;
            display: none;
            font-size: x-large;
            margin-bottom: 10px;
        }
    </style>
</head>
<body>
    <div class="baap">
    <h1>Expense Tracker</h1>
    <form>
        
        <input type="text" id="des" placeholder="Expense description"><br><br>
        <select id="select">
            <option value="none">Select catageory</option>
            <option value="Food">food</option>
            <option value="transportation">transportation</option>
            <option value="movie">movie</option>
            <option value="other">other</option>

        </select><br><br>
        <input type="number" id="amount" placeholder="Enter amount"><br><br>
        <button id="submit">Add Expense</button><br><br>
    </form>
    <div class="mess">First fill out all the empty feilds</div>
    <table border="2" callpadding="2" cellspacing="2" id="table">
        <thead>
            <tr>
        <th>description</th>
        <th>catageory</th>
        <th>amount</th>
        </tr>
        </thead>
    </table>
    </div>
</body>
<script>
    let taskArray=[];
    const submit=document.querySelector('#submit');
    const table=document.querySelector('#table');
    const mess=document.querySelector('.mess');
    let expl=localStorage.getItem("expl");
    if(expl)
    {
        taskArray=JSON.parse(expl);
    }
    taskArray.forEach((val)=>{
           let newr=document.createElement("tr");
           newr.innerHTML=`<td>${val.description}</td> <td>${val.cata}</td> <td>${val.amt}</td>`;
           table.appendChild(newr);

        })
    submit.addEventListener('click',function(event){

    
             event.preventDefault();
             const desa=document.querySelector('#des');
             const selecta=document.querySelector('#select');
             const amounta=document.querySelector('#amount'); 
             const des=document.querySelector('#des').value;
             const select=document.querySelector('#select').value;
             const amount=document.querySelector('#amount').value; 
             const newRow=document.createElement('tr');
             if(des==''||select==''||amount=='')
             {
                
                mess.style.display="block";

                setTimeout(() => {
                    mess.style.display='';

                }, 6000);

             }
             
             else{
               
             let obj={
              "description":des,
              "cata":select,
              "amt":amount,

            } 
             taskArray.push(obj);
             localStorage.setItem("expl",JSON.stringify(taskArray));
             newRow.innerHTML=`<td>${des}</td> <td>${select}</td> <td>${amount}</td>`;
             table.appendChild(newRow);
        }
             document.querySelector('#des').value='';
             document.querySelector('#select').value='';
             document.querySelector('#amount').value='';
    })

</script>
</html>
