# oppimis3.github.io
projektti
<!DOCTYPE html>
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1">
<link rel="stylesheet" href="tyyli3.css">
</head>
<body>
  

<div class="topnav" id="myTopnav">
  <div id="home">
  <a href="oppimis 3.html" class="active">Etusivu</a></div>
  <div id="digi">
  <a href="digi.html">Digi&nbsp;Cafe</a></div>
  <div id="palaveri">
  <a href="palaveri.html">Palaveri</a> </div>
  <div id="tyopaikat">
  <a href="tyopaikat.html">Työpaikat</a></div>
  <a href="javascript:void(0);" class="icon" onclick="myFunction()">
    <i class="fa fa-bars"></i>
  </a>
</div>

<div style="padding-left:16px">
  <h2>Responsive Topnav Example</h2>
  <p>Resize the browser window to see how it works.</p>
</div>
<div id="vastaus"></div>
<script>
  
fetch('https://jaakkola.github.io/json/digitekniikat.json') 
// Muunnetaan vastaus JSON muotoon 
.then(function (response) { 
return response.json(); }) 
// Käsitellään muunnettu (eli JSON muotoinen) vastaus 
.then(function (responseJson) { 
kerro(responseJson) ;  })

.catch(function (error) { 
document.getElementById("vastaus").innerHTML ="<p>Tietoa ei pystytä hakemaan</p>"; })

function kerro(data){
  let teksti="";
  teksti = "<h1>" + data.otsikko + "</h1>"; 
  teksti = teksti + "<p>" + data.kuvaus + "</p>";
  teksti = teksti + "<p><img src='" + data.kuva + "' alt='kuva' ></p>";
  teksti = teksti + "<h3>Opintojakso: " + data.opintojakso.nimi + "</h3>";
  teksti= teksti + "<p> Tunnus: "+ data.opintojakso.tunnus +"</p>";
  teksti= teksti + "<p> Opintopisteet: " + data.opintojakso.opintopisteet + "</p>";
  teksti = teksti + "<ul>" 
for(let i = 0; i < data.sisalto.length; i++) { 
teksti = teksti + "<li>" + data.sisalto[i] + "</li>"; } 
  teksti = teksti + "</ul>" 
//objektitaulukko
for(let i=0; i<data.tekniikat.length; i++){ 
teksti = teksti + "<li>" + data.tekniikat[i].aihe +" "+ "<a href='" +data.tekniikat[i].linkki
+"'>"+ data.tekniikat[i].linkki + "</a></li>"; }

  document.getElementById("vastaus").innerHTML =teksti;
  
}
fetch("omaa.json") 
// Muunnetaan vastaus JSON muotoon 
.then(function (response) { 
return response.json(); 
}) 
// Käsitellään muunnettu (eli JSON muotoinen) vastaus (((ei onnistunut)))
.then(function (responseJson) { 
// Testataan onnistuuko json-luku 
// jos onnistuu päivitetään tähän json-datan käsittelevän funktion kutsu 
document.getElementById("vastaus").innerHTML =  
"<p>Jatketaan harjoitusta</p>";  
}) 
// Jos tuli jokin virhe 
.catch(function (error) { 
document.getElementById("vastaus").innerHTML =  
"<p>Tietoa ei pystytä hakemaan</p>"; 
})
 
</script>

</body>
</html>
