<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SpendWise — Watch your spending grow</title>
<style>
@import url('https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,400;9..144,600;9..144,700;9..144,800&family=Manrope:wght@400;500;600;700;800&family=IBM+Plex+Mono:wght@400;500;600&display=swap');

:root{
  --ink:#0B2B20;
  --forest-950:#06180F;
  --forest-800:#0E3626;
  --forest-700:#144934;
  --forest-600:#1B5C42;
  --mint-50:#F3FBF6;
  --mint-100:#E4F4EA;
  --emerald:#00C46A;
  --emerald-600:#009F57;
  --gold:#E7B84B;
  --teal:#4FB0C6;
  --sage:#7FA492;
  --sage-dim:#A9C4B6;
  --line:#1F4B37;
  --radius:18px;
}
*{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth}
body{
  font-family:'Manrope',Arial,sans-serif;
  color:var(--ink);
  background:
    radial-gradient(circle at 1px 1px, rgba(255,255,255,.05) 1px, transparent 0) 0 0/26px 26px,
    linear-gradient(160deg,var(--forest-950) 0%,var(--forest-800) 45%,var(--forest-700) 100%);
  min-height:100vh;
}
::selection{background:var(--emerald);color:var(--forest-950)}
:focus-visible{outline:2px solid var(--emerald);outline-offset:3px;border-radius:6px}

header{
  padding:22px 6%;
  display:flex;justify-content:space-between;align-items:center;
  border-bottom:1px solid rgba(255,255,255,.08);
}
.brand{display:flex;align-items:center;gap:12px}
.mark{width:40px;height:40px;flex-shrink:0;filter:drop-shadow(0 4px 10px rgba(231,184,75,.35))}
.wordmark{font-family:'Fraunces',serif;font-weight:700;font-size:23px;color:var(--mint-50);letter-spacing:.2px}
.tag{font-size:12.5px;color:var(--sage-dim);margin-top:2px;font-weight:500}
.chip{
  display:flex;align-items:center;gap:7px;
  background:rgba(0,196,106,.12);border:1px solid rgba(0,196,106,.35);
  color:var(--emerald);font-size:12.5px;font-weight:700;letter-spacing:.3px;
  padding:8px 14px;border-radius:100px;
}
.chip::before{content:"";width:7px;height:7px;border-radius:50%;background:var(--emerald);box-shadow:0 0 0 4px rgba(0,196,106,.18)}

.container{max-width:1180px;margin:0 auto;padding:0 20px 70px}
.hero{padding:46px 0 28px;opacity:0;animation:fadeUp .7s ease forwards}
.hero h1{
  font-family:'Fraunces',serif;font-weight:700;font-size:clamp(30px,4vw,44px);
  color:var(--mint-50);line-height:1.15;max-width:640px;
}
.hero p{color:var(--sage-dim);margin-top:10px;font-size:15.5px;max-width:520px}

.cards{display:grid;grid-template-columns:repeat(3,1fr);gap:16px;margin:8px 0 26px}
.card{
  background:linear-gradient(160deg,var(--mint-50),var(--mint-100));
  border-radius:var(--radius);padding:22px 22px 20px;
  box-shadow:0 14px 30px rgba(4,20,13,.35);
  opacity:0;animation:fadeUp .6s ease forwards;
  position:relative;overflow:hidden;
}
.card::after{content:"";position:absolute;right:-18px;top:-18px;width:70px;height:70px;border-radius:50%;background:rgba(0,196,106,.09)}
.card:nth-child(1){animation-delay:.05s}.card:nth-child(2){animation-delay:.15s}.card:nth-child(3){animation-delay:.25s}
.card small{color:#5B7768;font-weight:700;letter-spacing:.3px;font-size:12px;text-transform:uppercase}
.amount{font-family:'IBM Plex Mono',monospace;font-size:29px;font-weight:600;margin-top:10px;color:var(--ink)}

.grid{display:grid;grid-template-columns:360px 1fr;gap:18px}
.panel{
  background:linear-gradient(160deg,var(--mint-50),var(--mint-100));
  border-radius:var(--radius);padding:24px;
  box-shadow:0 14px 30px rgba(4,20,13,.3);
  opacity:0;animation:fadeUp .6s ease forwards;position:relative;
}
.panel + .panel{margin-top:18px}
.panel h2{font-family:'Fraunces',serif;font-size:19px;font-weight:600;margin-bottom:6px;display:flex;align-items:center;gap:8px}
.panel .sub{font-size:12.5px;color:#5B7768;margin-bottom:16px}
.bracket{position:absolute;top:18px;right:20px;font-family:'IBM Plex Mono',monospace;color:#B9CFC2;font-size:13px;letter-spacing:2px;opacity:.7}

label{font-size:12.5px;font-weight:700;display:block;margin:14px 0 6px;color:#3E5B4C;letter-spacing:.2px}
input,select{
  width:100%;padding:11px 12px;border:1.5px solid #D3E4DA;border-radius:10px;
  font-size:14px;font-family:'Manrope',sans-serif;background:#fff;color:var(--ink);
  transition:border-color .15s ease, box-shadow .15s ease;
}
input:focus,select:focus{border-color:var(--emerald);box-shadow:0 0 0 4px rgba(0,196,106,.14);outline:none}
button{border:0;border-radius:10px;padding:11px 16px;font-weight:700;cursor:pointer;font-family:'Manrope',sans-serif;transition:transform .12s ease, filter .15s ease}
button:active{transform:translateY(1px) scale(.99)}
.primary{background:linear-gradient(135deg,var(--emerald),var(--emerald-600));color:#fff;width:100%;margin-top:18px;font-size:14.5px;box-shadow:0 8px 18px rgba(0,196,106,.35)}
.primary:hover{filter:brightness(1.06)}
.secondary{background:#EAF1EC;color:#2A4438}
.secondary:hover{background:#DEEAE2}
.danger{background:#FBE9E7;color:#B3402E}
.danger:hover{background:#F6D8D4}

.filters{display:flex;gap:10px;margin-bottom:15px}
.filters input{flex:1}
.filters select{width:160px}

table{width:100%;border-collapse:collapse}
th,td{text-align:left;padding:13px 10px;border-bottom:1px solid #E4EEE8;font-size:13.5px}
th{color:#6B8579;font-weight:700;text-transform:uppercase;font-size:11px;letter-spacing:.4px}
tbody tr{transition:background .12s ease}
tbody tr:hover{background:#F0F8F3}
td.amt{font-family:'IBM Plex Mono',monospace;font-weight:600}
.badge{padding:5px 10px;border-radius:20px;font-size:11.5px;font-weight:700;display:inline-block}
.b-Food{background:#E1F7EA;color:#0A8F53}
.b-Travel{background:#FBF1DC;color:#96731A}
.b-Shopping{background:#E3F3F7;color:#227087}
.b-Education{background:#EBF6E0;color:#5C8A2A}
.b-Other{background:#EAF0ED;color:#4C6459}
.actions button{padding:6px 10px;margin-right:5px;font-size:12px}

/* growth chart — spending rendered as growing stems */
.stems{display:flex;align-items:flex-end;gap:22px;min-height:210px;padding:10px 6px 0;overflow-x:auto}
.stem-col{display:flex;flex-direction:column;align-items:center;min-width:56px}
.stem-amt{font-family:'IBM Plex Mono',monospace;font-size:11.5px;font-weight:600;color:#3E5B4C;margin-bottom:6px;white-space:nowrap}
.stem-track{width:14px;height:150px;display:flex;align-items:flex-end;background:linear-gradient(#EAF2ED,#EAF2ED) center/2px 100% no-repeat}
.stem-fill{width:14px;border-radius:8px 8px 3px 3px;height:0;transition:height 1s cubic-bezier(.2,.8,.2,1);position:relative}
.stem-fill::after{content:"";position:absolute;top:-6px;left:50%;transform:translateX(-50%);width:11px;height:11px;border-radius:50%;background:inherit;box-shadow:0 0 0 3px rgba(255,255,255,.6)}
.stem-label{font-size:12px;font-weight:700;color:#3E5B4C;margin-top:10px}

.empty{text-align:center;color:#7A9186;padding:38px 20px;font-size:13.5px;line-height:1.6}
.empty b{display:block;color:#3E5B4C;font-size:14.5px;margin-bottom:4px;font-family:'Fraunces',serif}

footer{text-align:center;color:var(--sage-dim);font-size:12px;padding:30px 0 10px}
footer span{color:var(--emerald);font-weight:700}

/* modal */
.overlay{position:fixed;inset:0;background:rgba(6,24,15,.6);backdrop-filter:blur(3px);display:none;align-items:center;justify-content:center;z-index:50;padding:20px}
.overlay.open{display:flex}
.modal{background:var(--mint-50);border-radius:var(--radius);padding:26px;width:100%;max-width:380px;box-shadow:0 30px 60px rgba(0,0,0,.4)}
.modal h2{font-family:'Fraunces',serif;font-size:19px;margin-bottom:4px}
.modal .sub{font-size:12.5px;color:#5B7768;margin-bottom:4px}
.modal-actions{display:flex;gap:10px;margin-top:18px}
.modal-actions button{flex:1;margin-top:0}

@keyframes fadeUp{from{opacity:0;transform:translateY(14px)}to{opacity:1;transform:translateY(0)}}

@media(max-width:860px){
  .grid,.cards{grid-template-columns:1fr}
  .filters{flex-direction:column}
  .filters select{width:100%}
  header{flex-direction:column;gap:10px;align-items:flex-start}
}
@media(prefers-reduced-motion:reduce){
  *{animation-duration:.001s !important;transition-duration:.001s !important}
}
</style>
</head>
<body>
<header>
  <div class="brand">
    <svg class="mark" viewBox="0 0 40 40" fill="none" xmlns="http://www.w3.org/2000/svg">
      <circle cx="20" cy="20" r="20" fill="#0E3626"/>
      <circle cx="20" cy="20" r="14.5" fill="none" stroke="#E7B84B" stroke-width="2"/>
      <circle cx="20" cy="20" r="10.5" fill="none" stroke="#00C46A" stroke-width="1.2" stroke-dasharray="2 2.4"/>
      <text x="20" y="25.5" text-anchor="middle" font-family="'IBM Plex Mono',monospace" font-size="15" font-weight="600" fill="#F3FBF6">₹</text>
    </svg>
    <div>
      <div class="wordmark">SpendWise</div>
      <div class="tag">Track. Understand. Grow.</div>
    </div>
  </div>
  <div class="chip">🌱 Grow your savings</div>
</header>

<div class="container">
  <section class="hero">
    <h1>Where did your money go this month?</h1>
    <p>Log every rupee, spot the patterns, and watch your spending habits take shape — one entry at a time.</p>
  </section>

  <div class="cards">
    <div class="card"><small>Total Expenses</small><div class="amount" id="total">₹0</div></div>
    <div class="card"><small>This Month</small><div class="amount" id="month">₹0</div></div>
    <div class="card"><small>Transactions</small><div class="amount" id="count">0</div></div>
  </div>

  <div class="grid">
    <div>
      <div class="panel" style="animation-delay:.1s">
        <span class="bracket">{ }</span>
        <h2>➕ Add Expense</h2>
        <div class="sub">Every entry becomes a document in your ledger.</div>
        <label>Amount (₹)</label><input id="amount" type="number" min="1" placeholder="e.g. 250">
        <label>Category</label>
        <select id="category"><option>Food</option><option>Travel</option><option>Shopping</option><option>Education</option><option>Other</option></select>
        <label>Description</label><input id="description" placeholder="e.g. College lunch">
        <label>Payment Method</label>
        <select id="payment"><option>UPI</option><option>Cash</option><option>Card</option></select>
        <label>Date</label><input id="date" type="date">
        <button class="primary" onclick="addExpense()">Add Expense</button>
      </div>

      <div class="panel" style="animation-delay:.2s">
        <h2>📊 Category Breakdown</h2>
        <div class="sub">Each bar grows with what you've spent.</div>
        <div id="chart"></div>
      </div>
    </div>

    <div class="panel" style="animation-delay:.15s">
      <h2>Recent Transactions</h2>
      <div class="sub">Search, filter, and manage every entry.</div>
      <div class="filters">
        <input id="search" placeholder="Search expenses..." oninput="render()">
        <select id="filter" onchange="render()"><option>All</option><option>Food</option><option>Travel</option><option>Shopping</option><option>Education</option><option>Other</option></select>
      </div>
      <div style="overflow-x:auto">
        <table><thead><tr><th>Date</th><th>Category</th><th>Description</th><th>Payment</th><th>Amount</th><th>Action</th></tr></thead>
        <tbody id="list"></tbody></table>
      </div>
    </div>
  </div>

  <footer>Made with <span>SpendWise</span> · a MongoDB hackathon project</footer>
</div>

<div class="overlay" id="editOverlay">
  <div class="modal">
    <h2>Edit Expense</h2>
    <div class="sub">Update the details below.</div>
    <label>Amount (₹)</label><input id="editAmount" type="number" min="1">
    <label>Category</label>
    <select id="editCategory"><option>Food</option><option>Travel</option><option>Shopping</option><option>Education</option><option>Other</option></select>
    <label>Description</label><input id="editDescription">
    <label>Payment Method</label>
    <select id="editPayment"><option>UPI</option><option>Cash</option><option>Card</option></select>
    <label>Date</label><input id="editDate" type="date">
    <div class="modal-actions">
      <button class="secondary" onclick="closeEdit()">Cancel</button>
      <button class="primary" style="margin-top:0" onclick="saveEdit()">Save Changes</button>
    </div>
  </div>
</div>

<script>
let expenses=JSON.parse(localStorage.getItem("spendwise_expenses")||"[]");
document.getElementById("date").value=new Date().toISOString().slice(0,10);

const catColors={Food:"#00C46A",Travel:"#E7B84B",Shopping:"#4FB0C6",Education:"#7CC24A",Other:"#7FA492"};
let editingId=null;
let firstRender=true;

function save(){localStorage.setItem("spendwise_expenses",JSON.stringify(expenses));}

function addExpense(){
 const amount=Number(document.getElementById("amount").value);
 const category=document.getElementById("category").value;
 const description=document.getElementById("description").value.trim();
 const payment=document.getElementById("payment").value;
 const date=document.getElementById("date").value;
 if(!amount||!description||!date){alert("Please fill all fields.");return}
 expenses.unshift({id:Date.now(),amount,category,description,payment,date});
 save(); render();
 document.getElementById("amount").value="";document.getElementById("description").value="";
}

function del(id){expenses=expenses.filter(e=>e.id!==id);save();render();}

function editExpense(id){
 const e=expenses.find(x=>x.id===id); if(!e)return;
 editingId=id;
 document.getElementById("editAmount").value=e.amount;
 document.getElementById("editCategory").value=e.category;
 document.getElementById("editDescription").value=e.description;
 document.getElementById("editPayment").value=e.payment;
 document.getElementById("editDate").value=e.date;
 document.getElementById("editOverlay").classList.add("open");
}
function closeEdit(){document.getElementById("editOverlay").classList.remove("open");editingId=null;}
function saveEdit(){
 const e=expenses.find(x=>x.id===editingId); if(!e)return;
 const amount=Number(document.getElementById("editAmount").value);
 const description=document.getElementById("editDescription").value.trim();
 const date=document.getElementById("editDate").value;
 if(!amount||!description||!date){alert("Please fill all fields.");return}
 e.amount=amount;
 e.category=document.getElementById("editCategory").value;
 e.description=description;
 e.payment=document.getElementById("editPayment").value;
 e.date=date;
 save();closeEdit();render();
}

function animateValue(el,end,prefix){
 const start=0,duration=700,startTime=performance.now();
 function tick(now){
   const p=Math.min((now-startTime)/duration,1);
   const eased=1-Math.pow(1-p,3);
   const val=Math.round(start+(end-start)*eased);
   el.textContent=prefix+val.toLocaleString("en-IN");
   if(p<1)requestAnimationFrame(tick);
 }
 requestAnimationFrame(tick);
}

function render(){
 const search=document.getElementById("search").value.toLowerCase();
 const filter=document.getElementById("filter").value;
 const shown=expenses.filter(e=>
   (filter==="All"||e.category===filter) &&
   (e.description.toLowerCase().includes(search)||e.category.toLowerCase().includes(search))
 );
 document.getElementById("list").innerHTML=shown.length?shown.map(e=>`
 <tr><td>${e.date}</td><td><span class="badge b-${e.category}">${e.category}</span></td>
 <td>${e.description}</td><td>${e.payment}</td><td class="amt">₹${e.amount.toLocaleString("en-IN")}</td>
 <td class="actions"><button class="secondary" onclick="editExpense(${e.id})">Edit</button><button class="danger" onclick="del(${e.id})">Delete</button></td></tr>`).join("")
 :`<tr><td colspan="6"><div class="empty"><b>No expenses yet</b>Add your first one above to start tracking where it goes.</div></td></tr>`;

 const total=expenses.reduce((s,e)=>s+e.amount,0);
 const now=new Date(), month=now.getMonth(),year=now.getFullYear();
 const monthly=expenses.filter(e=>{let d=new Date(e.date);return d.getMonth()===month&&d.getFullYear()===year}).reduce((s,e)=>s+e.amount,0);

 if(firstRender){
   animateValue(document.getElementById("total"),total,"₹");
   animateValue(document.getElementById("month"),monthly,"₹");
   animateValue(document.getElementById("count"),expenses.length,"");
   firstRender=false;
 }else{
   document.getElementById("total").textContent="₹"+total.toLocaleString("en-IN");
   document.getElementById("month").textContent="₹"+monthly.toLocaleString("en-IN");
   document.getElementById("count").textContent=expenses.length;
 }

 const cats={};expenses.forEach(e=>cats[e.category]=(cats[e.category]||0)+e.amount);
 const max=Math.max(...Object.values(cats),1);
 const chartEl=document.getElementById("chart");
 if(!Object.keys(cats).length){
   chartEl.innerHTML="<div class='empty'><b>Nothing to show yet</b>Add an expense to see your spending grow.</div>";
 }else{
   const entries=Object.entries(cats).sort((a,b)=>b[1]-a[1]);
   chartEl.innerHTML=`<div class="stems">${entries.map(([c,v])=>`
     <div class="stem-col">
       <div class="stem-amt">₹${v.toLocaleString("en-IN")}</div>
       <div class="stem-track"><div class="stem-fill" data-h="${v/max*150}" style="background:${catColors[c]||'#7FA492'}"></div></div>
       <div class="stem-label">${c}</div>
     </div>`).join("")}</div>`;
   requestAnimationFrame(()=>{
     document.querySelectorAll(".stem-fill").forEach(el=>{
       el.style.height=el.dataset.h+"px";
     });
   });
 }
}
render();
</script>
</body>
</html>
