
[novoooooo4.html](https://github.com/user-attachments/files/24723557/novoooooo4.html)
<!DOCTYPE html>
<html lang="hr">
<head>
<meta charset="UTF-8">
<title>Teži kviz – Osnaživanje roditelja</title>
<style>
body {
    margin: 0;
    font-family: Arial, sans-serif;
    background-color: #1565c0;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    color: white;
}
.quiz {
    background: #0d47a1;
    padding: 30px;
    border-radius: 12px;
    width: 85%;
    max-width: 800px;
    text-align: center;
}
.option {
    background: white;
    color: black;
    padding: 12px;
    margin: 10px 0;
    border-radius: 6px;
    cursor: pointer;
}
.option:hover { background: #bbdefb; }
input[type="text"] { width: 80%; padding: 10px; margin-top: 10px; }
button { margin-top: 15px; padding: 10px 20px; font-size: 16px; cursor: pointer; }
.result { margin-top: 15px; font-weight: bold; }
.explanation { margin-top: 10px; font-size: 14px; }
</style>
</head>
<body>
<div class="quiz">
    <h2 id="question"></h2>
    <div id="answers"></div>
    <button id="checkBtn" style="display:none;">Provjeri</button>
    <div id="result" class="result"></div>
    <div id="explanation" class="explanation"></div>
</div>
<script>
const quiz = [
{type:"mc", q:"Koja kombinacija faktora najjače predviđa roditeljski stres prema Milić Babić (2012)?",
o:["Loša financijska situacija + niska socijalna podrška","Visoko obrazovanje + dobro zdravlje","Nedovoljno informacija + mala djeca","Ruralna sredina + religijska podrška"],
c:0, e:"Financijske poteškoće i nezadovoljstvo socijalnom podrškom objašnjavaju najveći dio varijance stresa."},

{type:"tf", q:"Kronični stres se javlja kada roditelj ne uspijeva uspostaviti održive mehanizme suočavanja.", c:true, e:"Kronični stres je dugotrajan i povezan s neuspjehom u strategijama suočavanja."},

{type:"mc", q:"Koja strategija suočavanja kombinira kognitivne i bihevioralne elemente te se pokazuje najučinkovitijom?",
o:["Pasivno prihvaćanje","Traženje podrške + aktivno rješavanje","Religijska molitva","Izbjegavanje problema"],
c:1, e:"Kombinacija traženja podrške i aktivnog rješavanja smanjuje stres i poboljšava kompetenciju roditelja."},

{type:"text", q:"Kako se na engleskom naziva koncept suočavanja sa stresom?", c:"coping", e:"U literaturi se koristi pojam coping za strategije suočavanja."},

{type:"mc", q:"Koji fenomen opisuje prelijevanje stresa iz roditeljske uloge u partnerski odnos?",
o:["Transverzalni stres","Spillover","Burnout","Sekundarni stres"],
c:1, e:"Fenomen prelaska stresa u druge domene života naziva se spillover."},

{type:"mc", q:"Koja od sljedećih tvrdnji je TOČNA o utjecaju roditeljskog stresa na obiteljsku koheziju?",
o:["Viši stres povećava bliskost","Viši stres smanjuje koheziju","Stres nema utjecaj","Stres poboljšava komunikaciju"],
c:1, e:"Istraživanja pokazuju negativnu korelaciju (-0,462) između stresa i obiteljske kohezije."},

{type:"tf", q:"Nepovjerenje roditelja može dovesti do kašnjenja intervencija.", c:true, e:"Nepovjerenje i nelagoda odgađaju traženje pomoći i smanjuju koordinaciju podrške."},

{type:"mc", q:"Koja vrsta podrške ima NAJJAČI zaštitni učinak na mentalno zdravlje roditelja?",
o:["Formalna + neformalna socijalna podrška","Financijska podrška","Radno mjesto s fleksibilnim satima","Samo institucionalna podrška"],
c:0, e:"Kombinacija formalne i neformalne podrške smanjuje stres i poboljšava dobrobit."},

{type:"text", q:"Koja osoba koordinira podršku roditeljima u sustavu rane intervencije?", c:"ključna osoba", e:"Ključna osoba koordinira komunikaciju i podršku između roditelja i stručnjaka."},

{type:"mc", q:"Koji čimbenik najviše doprinosi nelagodama u traženju stručne pomoći?",
o:["Negativna iskustva sa sustavom","Dob djeteta","Financijski status","Spol roditelja"],
c:0, e:"Negativna iskustva roditelja i nepovjerenje prema sustavu povećavaju nelagodu."},

{type:"tf", q:"Roditelji koriste kombinirane adaptivne strategije imaju nižu razinu stresa.", c:true, e:"Kombinacija podrške i aktivnog suočavanja smanjuje stres."},

{type:"mc", q:"Koja komponenta rane intervencije NIJE ključna?",
o:["Multidisciplinarni tim","Individualni plan podrške","Izoliran pristup bez koordinacije","Transparentnost"],
c:2, e:"Izolirani pristup nije u skladu s principima rane intervencije."},

{type:"mc", q:"Koji je najvažniji faktor u emocionalno osjetljivom radu odgojitelja?",
o:["Empatija i emocionalna prisutnost","Formalna autoritativnost","Stroga evaluacija","Izolacija roditelja"],
c:0, e:"Empatija i emocionalna prisutnost omogućuju učinkovitu suradnju s roditeljima."},

{type:"text", q:"Kako se zove proces u kojem stres iz roditeljstva prelazi u partnerski odnos?", c:"prelijevanje stresa", e:"Lazarević opisuje fenomen spillover/prelijevanja stresa."},

{type:"mc", q:"Koji problem roditelja je najizraženiji prema Međaković i sur. (2024)?",
o:["Previše informacija","Nedostatak informacija i slabija međuresorna suradnja","Jednaka kvaliteta usluga","Višak podrške"],
c:1, e:"Roditelji često ne znaju prava, usluge i procedura, te postoji slabija međuresorna suradnja."},

{type:"tf", q:"Kvaliteta podrške je jednaka u svim regijama Hrvatske.", c:false, e:"Postoje velike razlike između regija u kvaliteti podrške."},

{type:"mc", q:"Koji element jača povjerenje roditelja u sustav?",
o:["Kontinuitet, transparentnost, uključivanje","Formalna procedura bez komunikacije","Kritika roditelja","Ignoriranje pitanja"],
c:0, e:"Kontinuitet i transparentnost u radu sustava jačaju povjerenje roditelja."},

{type:"text", q:"Koji je glavni cilj osnaživanja roditelja?", c:"dobrobit roditelja", e:"Roditeljska dobrobit temelj je učinkovitog sustava podrške."},

{type:"mc", q:"Koja kombinacija faktora može najviše pogoršati mentalno zdravlje roditelja?",
o:["Dobra socijalna podrška + niska očekivanja","Loše zdravlje + nedostatak podrške","Visoko obrazovanje + aktivno suočavanje","Dobra financijska situacija + planiranje"],
c:1, e:"Loše subjektivno zdravlje i nedostatak podrške povećavaju rizik od pogoršanja mentalnog zdravlja."},

{type:"mc", q:"Koji je NAJvažniji faktor za uspješnu inkluziju u vrtiću?",
o:["Odgojitelj izoliran od roditelja","Vrtić kao integracijsko mjesto podrške","Nepostojanje koordinacije","Nedostatak multidisciplinarnog tima"],
c:1, e:"Vrtić kao čvorište podrške omogućuje povezivanje roditelja, stručnjaka i zajednice."}
];

let i=0, score=0;

function load(){
    const q=quiz[i];
    document.getElementById("question").innerText=(i+1)+". "+q.q;
    const a=document.getElementById("answers");
    a.innerHTML="";
    document.getElementById("result").innerText="";
    document.getElementById("explanation").innerText="";
    document.getElementById("checkBtn").style.display="none";

    if(q.type==="mc"){ q.o.forEach((opt, idx)=>{
        const d=document.createElement("div");
        d.className="option"; d.innerText=opt;
        d.onclick=()=>check(idx); a.appendChild(d);
    });}
    if(q.type==="tf"){ ["Točno","Netočno"].forEach((opt, idx)=>{
        const d=document.createElement("div");
        d.className="option"; d.innerText=opt;
        d.onclick=()=>check(idx===0); a.appendChild(d);
    });}
    if(q.type==="text"){ a.innerHTML=`<input type="text" id="txt">`;
        document.getElementById("checkBtn").style.display="inline";
        document.getElementById("checkBtn").onclick=()=>{
            const val=document.getElementById("txt").value.toLowerCase().trim();
            check(val);
        };
    }
}

function check(ans){
    const q=quiz[i];
    let correct=false;
    if(q.type==="mc") correct=ans===q.c;
    if(q.type==="tf") correct=ans===q.c;
    if(q.type==="text") correct=ans.includes(q.c.toLowerCase());
    if(correct){ score++; document.getElementById("result").innerText="Točno!";}
    else{ document.getElementById("result").innerText="Netočno."; document.getElementById("explanation").innerText=q.e;}
    setTimeout(()=>{
        i++;
        if(i<quiz.length) load();
        else document.querySelector(".quiz").innerHTML=`<h2>Kraj kviza</h2><p>Rezultat: ${score} / ${quiz.length}</p>`;
    },2500);
}

load();
</script>
</body>
</html>
