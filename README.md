<!DOCTYPE html>
<html lang="ar">
<head>
<meta charset="UTF-8">
<title>بطاقة فري فاير</title>

<style>
body{
  font-family: Arial;
  direction: rtl;
  background:#111;
  display:flex;
  justify-content:center;
  align-items:center;
  height:100vh;
}

.card{
  width:700px;
  background:white;
  border-radius:15px;
  padding:20px;
  box-shadow:0 0 20px rgba(0,0,0,0.5);
}

.header{
  text-align:center;
}

.header h2{
  color:red;
  margin:5px;
}

.row{
  display:flex;
  margin-top:15px;
}

.image-box{
  width:200px;
  height:250px;
  border:2px solid black;
  border-radius:10px;
  overflow:hidden;
  margin-left:15px;
  position:relative;
}

.image-box img{
  width:100%;
  height:100%;
  object-fit:cover;
}

.upload{
  position:absolute;
  bottom:5px;
  left:5px;
  background:black;
  color:white;
  font-size:12px;
  padding:3px 6px;
  cursor:pointer;
}

.info{
  flex:1;
}

.field{
  border-bottom:1px solid black;
  padding:10px;
  cursor:pointer;
}

input{
  width:100%;
  border:none;
  outline:none;
  font-size:16px;
}

button{
  margin-top:15px;
  width:100%;
  padding:10px;
  background:red;
  color:white;
  border:none;
  font-size:16px;
  cursor:pointer;
  border-radius:8px;
}
</style>

</head>

<body>

<div class="card" id="card">

  <div class="header">
    <p>بسم الله الرحمن الرحيم</p>
    <h2>جمهورية السودان</h2>
    <h3>بطاقة تعريف فري فاير</h3>
  </div>

  <div class="row">

    <div class="image-box">
      <img id="preview" src="https://via.placeholder.com/200x250">
      <input type="file" id="file" hidden>
      <div class="upload" onclick="upload()">📸 صورة</div>
    </div>

    <div class="info">
      <div class="field" onclick="edit(this)">اسم اللاعب</div>
      <div class="field" onclick="edit(this)">رقم ID</div>
      <div class="field" onclick="edit(this)">مستوى الحساب</div>
      <div class="field" onclick="edit(this)">تصنيف باتل رويال</div>
      <div class="field" onclick="edit(this)">تصنيف كلاش سكواد</div>
      <div class="field" onclick="edit(this)">أسلوب اللاعب</div>
      <div class="field" onclick="edit(this)">تاريخ إنشاء الحساب</div>
    </div>

  </div>

  <button onclick="download()">⬇️ تحميل البطاقة</button>

</div>

<script>
function edit(el){
  let text = el.innerText;
  el.innerHTML = `<input type="text" value="${text}" onblur="save(this)">`;
}

function save(input){
  input.parentElement.innerHTML = input.value;
}

function upload(){
  document.getElementById("file").click();
}

document.getElementById("file").addEventListener("change", function(e){
  let reader = new FileReader();
  reader.onload = function(){
    document.getElementById("preview").src = reader.result;
  }
  reader.readAsDataURL(e.target.files[0]);
});

function download(){
  html2canvas(document.getElementById("card")).then(canvas=>{
    let link = document.createElement("a");
    link.download = "card.png";
    link.href = canvas.toDataURL();
    link.click();
  });
}
</script>

<script src="https://html2canvas.hertzen.com/dist/html2canvas.min.js"></script>

</body>
</html>
