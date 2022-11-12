
let input = document.getElementById("inputTag");
let fileName = document.getElementById("fileName")
let inputFile= document.querySelector("input[type=file]").files[0];

if(!localStorage.date_number || !localStorage.month_number){
    localStorage.date_number =  new Date().getDate();
    localStorage.month_number = new Date().getMonth();
}  else if(new Date().getDate() != localStorage.date_number || localStorage.month_number != new Date().getMonth()){
    localStorage.number_of_uses = 0;
    localStorage.date_number =  new Date().getDate();
    localStorage.month_number = new Date().getMonth();
}

let block_sending = false;

input.addEventListener("change", ()=>{
    inputFile = document.querySelector("input[type=file]").files[0];

    let name_len = inputFile.name.length;
    console.log(name_len);
    
    if(inputFile.name.charAt(name_len-1) == "t" &&
       inputFile.name.charAt(name_len-2) == "x" &&
       inputFile.name.charAt(name_len-3) == "t" &&
       inputFile.name.charAt(name_len-4) == "."){
	fileName.innerText = inputFile.name;
	document.querySelector("#file_size_warnning").textContent = "";
	block_sending = false;
    }else{
	document.querySelector("#file_size_warnning").textContent = "الملف يجب ان يكون بصيغة .txt";
	block_sending = true;
    }
    
    console.log(block_sending)
})

document.querySelector("#form").addEventListener("submit", function(e){

    let date = new Date().getDate();
    console.log(date);
    if(!localStorage.number_of_uses) localStorage.number_of_uses = 0;
    else if(fileName.innerText != "" && localStorage.number_of_uses<=5 && inputFile.size <= 500000 && !block_sending)
	localStorage.number_of_uses++;
    console.log(localStorage.number_of_uses);
    //e.preventDefault();

    if(block_sending){
	e.preventDefault();

    }
    
    if(localStorage.number_of_uses>5 && fileName.innerText != ""){
	e.preventDefault();
	document.querySelector("#file_size_warnning").textContent = "تم تجاوز الحد الاقصى لعدد الاستعمال اليومي"
    }
    if(fileName.innerText == ""){
	e.preventDefault();
	document.querySelector("#file_size_warnning").textContent = "اختر ملف النص اولا"
	
    }
    
    if(inputFile.size > 500000){
	e.preventDefault();
	document.querySelector("#file_size_warnning").textContent = "حجم الملف اكبر من الحجم المسموح به"
    }

    //console.log()
    
});
