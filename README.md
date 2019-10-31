# javascript-todo
js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Javascript todo</title>
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css">
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.7/umd/popper.min.js"></script>
  <script src="https://maxcdn.bootstrapcdn.com/bootstrap/4.3.1/js/bootstrap.min.js"></script>
</head>
<body>
    <div class="row">
    <div class="col-3"></div>
    <div class="card col-6 mt-4">

            <h1 class="text-danger ">Todo's</h1>
            <label for="items">Add item</label>
            <input type="text" id="items"><br>
            <button onclick="saveInput()" class="btn btn-success">Add</button>

        </div>
        <div class="col-3"></div>
    </div>

    <div class="row ml-4">
        <table id="userTable" class="table-bordered"></tr>
           
        </table>
    </div>
 <div class="row">
     <div class="col-3"></div>
     <div class="col-3 mt-4"><button class="btn btn-danger" id="del" onclick="deleteAll()">Delete All</button></div>
     <div class="col-3"></div>
     
 </div>
</body>
</html>
 <script>
     var arrayLists=[];
function saveInput(){ 
    var userInput=document.getElementById("items").value;
    arrayLists.push(userInput);
    localStorage.setItem("ListItems",arrayLists);
    displayData();
    // console.log(arrayLists);
}


function displayData(){
    document.getElementById("userTable").innerHTML="";
   var getDataArray=localStorage.getItem("ListItems");
    if(getDataArray){
        getDataArray=getDataArray.split(',');
        arrayLists=getDataArray;
        document.getElementById("userTable").innerHTML+="<tr><th> Index </th><th>Items</th><th>Delete</th></tr>";
    }
    else  getDataArray=[];
    console.log(getDataArray);
    for(var i=0;i<getDataArray.length;i++){
        document.getElementById("userTable").innerHTML+="<tr><td>"+i+"</td><td>"+getDataArray[i]+"</td><td><button onclick=deleteItem("+i+") class='btn btn-primary'>Delete</button></td></tr>";
    }
}
function deleteItem(key){
    arrayLists.splice(key,1);
    localStorage.setItem("ListItems",arrayLists);
    displayData();
}
function deleteAll(){
    localStorage.removeItem("ListItems");
    arrayLists=[];
    displayData();
}
displayData();
</script>
