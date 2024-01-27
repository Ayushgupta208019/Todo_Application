<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Todo Application by Ayush Gupta</title>
    <style>
        body{
            background: rgb(63,94,251);
            background: radial-gradient(circle, rgba(63,94,251,1) 0%, rgba(252,70,107,1) 100%);
        }
        #date{
            color: white;
            text-align: center;
        }
        .pri{
            text-align: center;
        }
        #print_btn{
            width: 100px;
            height: 30px;
            background-color: greenyellow;
            color: red;
            font-size: 15px;
            font-weight: bolder;
            border-radius: 5px;
            border-color: green;
        }
        #print_btn:hover{
            background-color: green;
            cursor: pointer;
            color: white;
        }
        .main_content{
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            margin-top: 20px;
        }
        input{
            text-align: center;
            width: 200px;
            background-color: aqua;
            height: 35px;
            font-size: 20px;
            font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
            color: blueviolet;
        }
        #add_btn{
            text-align: center;
            width: 100px;
            height: 50px;
            background-color: greenyellow;
            color: red;
            font-size: 15px;
            font-weight: bolder;
            border-radius: 5px;
            border-color: green;
        }
        #add_btn:hover{
            background-color: green;
            cursor: pointer;
            color: white;
        }

        #data-show{
            margin-top: 20px;
        }
        img{
            width: 20px;
            background-color: red;
        }

    </style>
</head>
<body>
    <div class="date">
        <h1 id="date"></h1>
    </div>
    <div class="pri">
        <button onclick="printTodo()" id="print_btn">Print Todo</button>
        <marquee behavior="" direction="" id="marquee" style="color: white;"><img src="img/images.jpeg" alt="">Note:- For Best View Please Print This TODO LIST in LandScape Mode, Thank You!!</marquee>
    </div>

    <div class="main_content">
    <div class="container">
        <input type="text" name="todoInput" id="todoInput">
        <input type="time" name="startlineInput" id="startlineInput">
        <input type="time" name="deadlineInput" id="deadlineInput">
        <button type="button" onclick="addTodo()" id="add_btn">Add Task</button>
    </div>

    <div class="data-show" id="data-show">
        <table border="2px solid" id="data-table" width="900px" style="font-size: 30px;">
            <tbody id="tbody">
            <tr style="background-color: greenyellow;">
            <th>Todo Detail</th>
            <th>Start Time/Date</th>
            <th>End Time/Date</th>
            </tr>
            </tbody>
        </table>
    </div>
    </div>

    <script>

        const TODO_DATE = new Date();
        let date = TODO_DATE.getDate()
        let year = TODO_DATE.getFullYear()
        let month = TODO_DATE.getMonth()
        //console.log(todo_date); Date testing Result Passed
        document.getElementById('date').innerHTML = `Today's Date is:- ${date}- ${month+1} -${year}`;

        function addTodo(){
            const TODO_DATA = document.getElementById('todoInput').value;
            const  START_TIME = document.getElementById('startlineInput').value;
            const  DEAD_TIME = document.getElementById('deadlineInput').value;
            let todoDetail ={
                detail : TODO_DATA,
                start_time: START_TIME,
                dead_time: DEAD_TIME
            }
            // Show Data in Table
            
            let table_body = document.getElementById('tbody');
            let row = document.createElement('tr');
            table_body.appendChild(row);
            row.style.backgroundColor= 'yellow';
            row.style.textAlign= 'center';
            row.style.fontFamily = "Impact, Haettenschweiler, 'Arial Narrow Bold', sans-seri";

            let td1 = document.createElement('td');
            
            td1.innerHTML = todoDetail.detail;
            row.appendChild(td1);

            let td2 = document.createElement('td');
            td2.innerHTML = todoDetail.start_time;
            row.appendChild(td2);

            let td3 = document.createElement('td');
            td3.innerHTML = todoDetail.dead_time;
            row.appendChild(td3);

           // console.log(table); testing completed result passed
        }

        function printTodo(){
            var mar = document.getElementById('marquee');
            //console.log(mar); Testing Result Passed
            mar.style.display= 'none';

            var btn = document.getElementById('print_btn');
            btn.style.display = 'none';

            var content = document.getElementsByClassName('container');
            for(var i = 0; i < content.length; i++){
                content[i].style.display = 'none';
            }

            window.print();
        }
    </script>
</body>
</html>
