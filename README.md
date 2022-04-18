# project-mapthapa
f
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="ccc.css">
</head>
<body>
    <div>
        <input type="text" id="contact"/>
        <button onClick="checkInput()">Submit</button>
        </div>
    
    <div id="container">

    </div>
    
    <script>
        const checkInput=()=>{
        const ee=document.getElementById('contact').value;
        console.log(ee);
        const container=document.querySelector('#container');
        const request=new XMLHttpRequest();
        request.open('GET', `https://restcountries.com/v3.1/name/${ee}`)
        request.send();
        //to get response
        request.addEventListener('load',function(){
           const [data]= JSON.parse(this.responseText)   
           console.log('done')
           const x=data.flags
           const x2=data.languages
           //console.log(x2)
           let str="";
           for(let property in x2)
           {
               str+=`${property},`;
            //console.log(property);   
           }

           console.log(str);
           console.log(typeof(x2))
          
           const idd=`<div id="card">
            <article class="card">
                <div class="card-body">
                <img src="${x.png}" alt="" class="card-body-image"/>
                <h1 class="card-body-title">${data.name.common}<span></span>
                </h1>
                <p class="card-body-text">capital: ${data.capital}</p>
             </div>
             <div class="class-footer">
                 <div class="card-footer-social">
                     <h3>${data.nativename}</h3>
                     <p>native lang</p>
                 </div>
                 <div class="card-footer-social">
                     <h3>${data.nativename}</h3>
                     <p>native lang</p>
                 </div>
                 <div class="card-footer-social">
                     <h3>${data.nativename}</h3>
                     <p>native lang</p>
                 </div>
             </div>
         </article>
     </div>`;
     container.insertAdjacentHTML("afterbegin",idd)
        })}
    </script>
</body>
</html>
