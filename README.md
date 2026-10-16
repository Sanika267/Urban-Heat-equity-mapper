<!DOCTYPE html>
<html lang="en"><head><meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Urban Heat Equity Mapper — Pune</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Sora:wght@400;600;700&family=Inter:wght@400;500&display=swap" rel="stylesheet">
<style>
:root{--bg:#f6f4ef;--card:#fff;--ink:#17201c;--mut:#5d6b64;--line:#e2ded3;--acc:#0f766e;--hot:#d9480f;--shadow:0 6px 24px rgba(20,30,25,.08);box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media(prefers-color-scheme:dark){:root:not([data-theme=light]){--bg:#0e1311;--card:#161d1a;--ink:#eaf1ed;--mut:#93a39a;--line:#26322d;--acc:#2dd4bf;--hot:#fb923c;--shadow:0 6px 24px rgba(0,0,0,.4)}}
:root[data-theme=dark]{--bg:#0e1311;--card:#161d1a;--ink:#eaf1ed;--mut:#93a39a;--line:#26322d;--acc:#2dd4bf;--hot:#fb923c;--shadow:0 6px 24px rgba(0,0,0,.4)}
html{scroll-padding-top:env(safe-area-inset-top,0px);scroll-behavior:smooth}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--ink);font:15px/1.6 Inter,system-ui,sans-serif}
h1,h2,h3{font-family:Sora,system-ui,sans-serif;line-height:1.2;margin:0}
a{color:var(--acc)}
.wrap{max-width:1180px;margin:0 auto;padding:0 20px}
nav{position:sticky;top:env(safe-area-inset-top,0px);z-index:10;background:color-mix(in srgb,var(--bg) 88%,transparent);backdrop-filter:blur(10px);border-bottom:1px solid var(--line)}
nav .wrap{display:flex;align-items:center;justify-content:space-between;height:58px;gap:12px}
.logo{font:700 16px Sora,sans-serif;display:flex;gap:8px;align-items:center}
.logo i{width:22px;height:22px;border-radius:50%;background:conic-gradient(#facc15,#fb923c,#dc2626,#7f1d1d,#facc15)}
nav .links{display:flex;gap:18px;align-items:center;font-size:14px}
nav .links a{color:var(--mut);text-decoration:none}nav .links a:hover{color:var(--ink)}
button{font:inherit;cursor:pointer}
#citySelect{font:inherit;cursor:pointer;max-width:150px}
@media(max-width:900px){nav .links{display:flex;flex-wrap:wrap;gap:10px}#citySelect{max-width:125px}}
.tbtn{border:1px solid var(--line);background:var(--card);color:var(--ink);border-radius:8px;padding:5px 10px}
.hero{padding:56px 0 28px;background:radial-gradient(900px 300px at 80% -10%,color-mix(in srgb,var(--hot) 22%,transparent),transparent)}
.tag{display:inline-block;font-size:12px;letter-spacing:.08em;text-transform:uppercase;color:var(--acc);border:1px solid var(--line);padding:4px 10px;border-radius:99px;background:var(--card)}
.hero h1{font-size:clamp(30px,5vw,52px);margin:14px 0;max-width:800px}
.hero h1 span{background:linear-gradient(90deg,#facc15,#ea580c,#dc2626);-webkit-background-clip:text;background-clip:text;color:transparent}
.hero p{max-width:640px;color:var(--mut);font-size:17px}
.stats{display:grid;grid-template-columns:repeat(4,1fr);gap:12px;margin-top:28px}
.stat,.card{background:var(--card);border:1px solid var(--line);border-radius:14px;box-shadow:var(--shadow)}
.stat{padding:14px 16px}.stat b{font:700 26px Sora,sans-serif;display:block}.stat small{color:var(--mut)}
section{padding:36px 0}
section>.wrap>h2{font-size:26px;margin-bottom:6px}.sub{color:var(--mut);margin:0 0 18px}
.app{display:grid;grid-template-columns:1.5fr 1fr;gap:18px}
.card{padding:16px}
.tabs{display:flex;flex-wrap:wrap;gap:6px;margin-bottom:10px}
.tabs button{border:1px solid var(--line);background:transparent;color:var(--ink);border-radius:99px;padding:5px 12px;font-size:13px}
.tabs button.on{background:var(--acc);color:#fff;border-color:var(--acc)}
.map{width:100%;height:auto;display:block;border-radius:10px;background:color-mix(in srgb,var(--bg) 70%,var(--card))}
.ward{stroke:var(--card);stroke-width:2.5;cursor:pointer;transition:filter .15s,stroke-width .15s;outline:none}
.ward:hover,.ward:focus{filter:brightness(1.12);stroke:var(--ink);stroke-width:3}
.ward.sel{stroke:var(--ink);stroke-width:4}
.lbl{font:600 10.5px Sora,sans-serif;fill:#111;pointer-events:none;text-anchor:middle;paint-order:stroke;stroke:rgba(255,255,255,.55);stroke-width:2.5px}
.lbl2{font:600 8.5px Inter,sans-serif;fill:#111;text-anchor:middle;paint-order:stroke;stroke:#fff;stroke-width:3px;stroke-linejoin:round}
.legend{display:flex;align-items:center;gap:8px;font-size:12px;color:var(--mut);margin-top:10px}
.legend i{flex:1;height:8px;border-radius:9px;max-width:220px}
.note{font-size:12px;color:var(--mut);margin-top:8px}
.panel h3{font-size:21px}
.badge{display:inline-block;padding:2px 10px;border-radius:99px;font-size:12px;font-weight:600;color:#fff;margin:8px 0}
.tiles{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin:10px 0}
.tile{border:1px solid var(--line);border-radius:10px;padding:8px 10px}.tile b{font:700 18px Sora,sans-serif;display:block}.tile small{color:var(--mut);font-size:12px}
.chips{display:flex;flex-wrap:wrap;gap:6px;margin:6px 0 12px}
.chips span{font-size:12.5px;border:1px solid var(--line);border-radius:99px;padding:2px 10px;background:color-mix(in srgb,var(--acc) 8%,transparent)}
.panel h4{margin:12px 0 4px;font:600 13px Sora,sans-serif;color:var(--mut);text-transform:uppercase;letter-spacing:.06em}
input[type=range]{width:100%;accent-color:var(--acc)}
.sim{border:1px dashed var(--acc);border-radius:10px;padding:10px 12px}
.rank{display:grid;grid-template-columns:repeat(auto-fill,minmax(260px,1fr));gap:8px}
.rk{display:flex;align-items:center;gap:10px;width:100%;text-align:left;border:1px solid var(--line);background:var(--card);color:var(--ink);border-radius:10px;padding:8px 10px}
.rk:hover{border-color:var(--acc)}.rk em{font:700 13px Sora;width:22px;color:var(--mut);font-style:normal}
.rk .n{flex:1;font-size:14px}.rk .bar{width:60px;height:6px;border-radius:9px;background:var(--line);overflow:hidden}.rk .bar i{display:block;height:100%}
.steps{display:grid;grid-template-columns:repeat(4,1fr);gap:12px}
.steps .card h3{font-size:16px;margin:6px 0}.steps p{margin:0;color:var(--mut);font-size:14px}
.num{width:30px;height:30px;border-radius:50%;background:var(--acc);color:#fff;display:grid;place-items:center;font:700 14px Sora}
.vals{display:grid;grid-template-columns:repeat(3,1fr);gap:12px;margin-top:14px}
footer{border-top:1px solid var(--line);padding:26px 0;color:var(--mut);font-size:13px}
footer .wrap{display:flex;justify-content:space-between;flex-wrap:wrap;gap:10px}
@media(max-width:900px){.app{grid-template-columns:1fr}.stats,.steps{grid-template-columns:1fr 1fr}.vals{grid-template-columns:1fr}nav .links a{display:none}}
</style></head><body>
<nav><div class="wrap"><div class="logo"><i></i>Heat Equity Mapper</div>
<div class="links"><label for="citySelect" style="font-size:13px;color:var(--mut)">City</label><select id="citySelect" class="tbtn" aria-label="Select city"><option value="Pune">Pune</option><option value="Nagpur">Nagpur</option><option value="Mumbai">Mumbai</option><option value="Thane">Thane</option><option value="Navi Mumbai">Navi Mumbai</option><option value="Pimpri-Chinchwad">Pimpri-Chinchwad</option><option value="Nashik">Nashik</option><option value="Chhatrapati Sambhajinagar">Chhatrapati Sambhajinagar</option><option value="Solapur">Solapur</option><option value="Kolhapur">Kolhapur</option><option value="Amravati">Amravati</option><option value="Akola">Akola</option><option value="Jalgaon">Jalgaon</option><option value="Dhule">Dhule</option><option value="Ahilyanagar">Ahilyanagar</option><option value="Sangli-Miraj-Kupwad">Sangli-Miraj-Kupwad</option><option value="Malegaon">Malegaon</option><option value="Nanded-Waghala">Nanded-Waghala</option><option value="Latur">Latur</option><option value="Parbhani">Parbhani</option><option value="Bhiwandi-Nizampur">Bhiwandi-Nizampur</option><option value="Mira-Bhayandar">Mira-Bhayandar</option><option value="Kalyan-Dombivli">Kalyan-Dombivli</option><option value="Ulhasnagar">Ulhasnagar</option><option value="Vasai-Virar">Vasai-Virar</option><option value="Panvel">Panvel</option><option value="Ichalkaranji">Ichalkaranji</option><option value="Jalna">Jalna</option><option value="Chandrapur">Chandrapur</option></select><a href="#map" id="mapNav">Pune Map</a><a href="#rank">Ranking</a><a href="#method">Method</a><button class="tbtn" id="theme" aria-label="Toggle theme">◐ Theme</button></div></div></nav>

<header class="hero"><div class="wrap">
<span class="tag">SDG 11 · SDG 13 · Climate Justice</span>
<h1>Who feels the heat <span>most?</span> Mapping urban heat inequality, ward by ward.</h1>
<p>An AI-based Urban Heat Equity Assessment Framework that fuses satellite imagery, land-surface temperature and demographic data to show which neighbourhoods carry the heaviest heat burden — built for municipal corporations. City selector covers Maharashtra municipal corporations. The map keeps the same original visual style.</p>
<div class="stats" id="stats"></div></div></header>

<section id="map"><div class="wrap">
<h2>Maharashtra neighbourhood heat explorer</h2>
<p class="sub">Select a city. The same stylised map design is reused for every city; region outlines and metrics are a demo template, not official municipal boundaries or measured city data.</p>
<div class="app">
<div class="card">
<div class="tabs" id="tabs" role="tablist"></div>
<svg class="map" id="svg" viewBox="0 0 600 440" role="img" aria-label="Stylised map of neighbourhood regions"></svg>
<div class="legend"><span id="lmin"></span><i id="lbar"></i><span id="lmax"></span></div>
<p class="note">Stylised map: ward territories are positioned to approximate real Pune geography (Mula–Mutha river, hills and arterial roads), not surveyed boundaries. Select a ward to pin its localities. Ward values are <b>illustrative sample data</b> for demonstration — replace with your pipeline's output (Landsat/Sentinel LST, canopy from CV, census data).</p>
</div>
<aside class="card panel" id="panel" aria-live="polite"></aside>
</div></div></section>

<section id="rank"><div class="wrap">
<h2>Equity priority ranking</h2>
<p class="sub">Heat Equity Index (HEI) blends surface temperature, missing tree canopy and social vulnerability. Higher = act first.</p>
<div class="rank" id="ranklist"></div></div></section>

<section id="method"><div class="wrap">
<h2>How it works</h2><p class="sub">GIS + satellite computer vision + demographic analytics.</p>
<div class="steps">
<div class="card"><div class="num">1</div><h3>Ingest imagery</h3><p>Satellite bands and thermal data pulled for the city boundary and tiled for analysis.</p></div>
<div class="card"><div class="num">2</div><h3>Vision analysis</h3><p>OpenCV segments tree cover, built-up area and bare surface; LST is derived per pixel.</p></div>
<div class="card"><div class="num">3</div><h3>Spatial indexing</h3><p>Quadtrees in PostGIS make ward- and block-level joins with census data fast.</p></div>
<div class="card"><div class="num">4</div><h3>Equity scoring</h3><p>HEI = 45% heat + 25% canopy deficit + 30% vulnerability, mapped in Mapbox.</p></div></div>
<div class="vals"><div class="card"><h3>Unity</h3><p class="sub" style="margin:4px 0 0">One shared evidence base for citizens, planners and researchers.</p></div>
<div class="card"><h3>Protector</h3><p class="sub" style="margin:4px 0 0">Prioritises the elderly, children and outdoor workers at highest risk.</p></div>
<div class="card"><h3>Respect</h3><p class="sub" style="margin:4px 0 0">Every neighbourhood is measured by the same transparent method.</p></div></div>
</div></section>

<footer><div class="wrap"><span>AI Based Urban Heat Equity Assessment Framework · ECO-07 · BVCOE – CS</span><span>Stack: Python · OpenCV · PostGIS · Mapbox</span></div></footer>

<script>
// id,name,row,col,pop(k),LST°C,canopy%,density(k/km²),vulnerability,localities
let W=[
["Aundh-Baner",0,0,420,38.2,21,9.8,38,["Aundh","Baner","Balewadi","Pashan","Sus"]],
["Shivajinagar-Ghole Road",0,1,360,39.6,17,14.2,44,["Shivajinagar","Deccan Gymkhana","FC Road","Model Colony","Bhamburda"]],
["Dhole Patil Road",0,2,340,40.1,15,13.5,47,["Pune Station","Koregaon Park","Bund Garden","Sangamwadi"]],
["Yerawada-Kalas-Dhanori",0,3,480,41.4,9,16.8,71,["Yerawada","Kalas","Dhanori","Vishrantwadi","Lohegaon"]],
["Nagar Road-Wadgaon Sheri",0,4,520,40.3,14,12.1,52,["Viman Nagar","Kalyani Nagar","Wadgaon Sheri","Kharadi","Tingre Nagar"]],
["Kothrud-Bavdhan",1,0,450,37.6,24,10.3,33,["Kothrud","Bavdhan","Erandwane","Paud Road","Mayur Colony"]],
["Kasba-Vishrambaug Wada",1,1,280,42.3,6,27.5,74,["Kasba Peth","Shaniwar Wada","Vishrambaug Wada","Budhwar Peth","Raviwar Peth"]],
["Bhavani Peth",1,2,310,42.9,5,29.1,82,["Bhavani Peth","Ganj Peth","Nana Peth","Ghorpade Peth","Kasewadi"]],
["Wanowrie-Ramtekdi",1,3,400,41.0,11,15.4,66,["Wanowrie","Ramtekdi","Fatima Nagar","Salunke Vihar"]],
["Hadapsar-Mundhwa",1,4,560,41.8,10,14.9,69,["Hadapsar","Mundhwa","Magarpatta","Manjri","Fursungi"]],
["Warje-Karvenagar",2,0,410,38.0,22,9.6,40,["Warje","Karve Nagar","Ram Nagar","Malwadi","Shivane"]],
["Sinhagad Road",2,1,440,39.0,19,11.7,46,["Sinhagad Road","Dhayari","Vadgaon Budruk","Nanded City","Hingne"]],
["Tilak Road",2,2,300,41.2,10,21.8,58,["Swargate","Sadashiv Peth","Narayan Peth","Parvati","Tilak Road"]],
["Dhankawadi-Sahakarnagar",2,3,430,40.7,13,16.2,63,["Dhankawadi","Sahakarnagar","Katraj","Bibwewadi","Ambegaon"]],
["Kondhwa-Yewalwadi",2,4,470,40.9,12,13.6,68,["Kondhwa","Yewalwadi","NIBM Road","Undri","Mohammadwadi"]]
].map((a,i)=>{const o={id:i,name:a[0],r:a[1],c:a[2],pop:a[3],lst:a[4],can:a[5],den:a[6],vul:a[7],loc:a[8]};o.hei=hei(o.lst,o.can,o.vul);return o});

const PUNE_W=W.map(w=>({...w,loc:[...w.loc]}));
const NAGPUR_RAW=[
["Mankapur",0,0,330,39.5,21,8.5,40,["Mankapur","Zingabai Takli","Gorewada"]],
["Civil Lines",0,1,290,38.6,27,7.2,31,["Civil Lines","High Court area","Ravi Nagar"]],
["Sadar",0,2,360,39.7,19,9.5,43,["Sadar","Kamptee Road","Gaddigodam"]],
["Mahal",0,3,420,41.2,12,15.0,59,["Mahal","Itwari","Gandhibagh"]],
["Sitabuldi",0,4,400,42.0,10,18.0,63,["Sitabuldi","Variety Square","Zero Mile"]],
["Trimurti Nagar",1,0,310,39.2,22,8.0,39,["Trimurti Nagar","Bhamti","Pratap Nagar"]],
["Pratap Nagar",1,1,350,39.8,18,10.5,46,["Pratap Nagar","Khamla","Somalwada"]],
["Dhantoli",1,2,380,40.1,17,11.0,48,["Dhantoli","Ramdaspeth","Congress Nagar"]],
["Itwari",1,3,450,41.5,11,16.0,64,["Itwari","Maskasath","Kalamna Road"]],
["Nandanvan",1,4,390,40.7,13,13.5,57,["Nandanvan","Hudkeshwar Road","Prajapati Nagar"]],
["Hingna",2,0,320,40.8,16,9.0,50,["Hingna","Wanadongri","MIDC Hingna"]],
["Manish Nagar",2,1,350,40.5,17,8.5,47,["Manish Nagar","Somalwada","Besa Road"]],
["MIHAN",2,2,300,41.5,13,6.5,54,["MIHAN","Airport area","Khapri"]],
["Besa",2,3,340,40.6,15,7.8,51,["Besa","Beltarodi","Pipla"]],
["Wardhaman Nagar",2,4,370,41.0,12,14.0,60,["Wardhaman Nagar","Pardi","Kapsi"]]
].map((a,i)=>{const o={id:i,name:a[0],r:a[1],c:a[2],pop:a[3],lst:a[4],can:a[5],den:a[6],vul:a[7],loc:a[8]};o.hei=hei(o.lst,o.can,o.vul);return o});
const NAGPUR_W=NAGPUR_RAW;
const CITY_AREAS={"Mumbai": ["Colaba", "Dadar", "Bandra", "Andheri", "Borivali", "Kurla", "Goregaon", "Mulund", "Chembur", "Byculla", "Worli", "Vikhroli", "Powai", "Malad", "Dahisar"], "Thane": ["Thane West", "Thane East", "Majiwada", "Kopri", "Wagle Estate", "Vartak Nagar", "Ghodbunder Road", "Manpada", "Kalwa", "Mumbra", "Kolshet", "Balkum", "Kasarvadavali", "Uthalsar", "Naupada"], "Navi Mumbai": ["Vashi", "Nerul", "Belapur", "Kharghar", "Airoli", "Ghansoli", "Koparkhairane", "Sanpada", "Juinagar", "Turbhe", "Seawoods", "CBD Belapur", "Kamothe", "Panvel Road", "Digha"], "Pimpri-Chinchwad": ["Pimpri", "Chinchwad", "Akurdi", "Nigdi", "Bhosari", "Moshi", "Chikhali", "Ravet", "Wakad", "Thergaon", "Pimple Saudagar", "Pimple Gurav", "Dapodi", "Sangvi", "Talawade"], "Nashik": ["Panchavati", "Nashik Road", "Satpur", "Cidco", "Indira Nagar", "Gangapur Road", "College Road", "Deolali", "Pathardi Phata", "Ambad", "Makhmalabad", "Adgaon", "Dwarka", "Govind Nagar", "Mhasrul"], "Chhatrapati Sambhajinagar": ["CIDCO", "Garkheda", "Osmanpura", "Seven Hills", "Waluj", "Satara Parisar", "Jalna Road", "Paithan Road", "Begumpura", "Shahgunj", "Mukundwadi", "Chikalthana", "Harsul", "Naregaon", "Padegaon"], "Solapur": ["Akkalkot Road", "Hotgi Road", "Jule Solapur", "Saat Rasta", "Siddheshwar Peth", "Navi Peth", "Muraarji Peth", "Vijapur Road", "Majrewadi", "Shelgi", "Kumtha Naka", "Railway Lines", "Ashok Chowk", "Laxmi Peth", "Degaon"], "Kolhapur": ["Rajarampuri", "Shahupuri", "Tarabai Park", "Rankala", "Uchgaon", "Rukmini Nagar", "Mangalwar Peth", "Laxmipuri", "Kasba Bawada", "Kadamwadi", "Shivaji Peth", "Phulewadi", "Sane Guruji Vasahat", "Udyamnagar", "Kalamba"], "Amravati": ["Rajapeth", "Badnera", "Camp", "Gadge Nagar", "Dastur Nagar", "Shegaon Naka", "Rukhmini Nagar", "Sai Nagar", "Walcut Compound", "Navathe", "Congress Nagar", "VMV Road", "Rahul Nagar", "Biyani Square", "Kathora Road"], "Akola": ["Jatharpeth", "Tapadia Nagar", "Ramdaspeth", "Gorakshan Road", "Mothi Umri", "Old City", "Naya Nagar", "Kaulkhed", "Umari", "Malkapur", "Shivani", "Dabki Road", "Civil Lines", "Khadki", "Washim Bypass"], "Jalgaon": ["Mehrun", "Shivaji Nagar", "Ring Road", "Ramanand Nagar", "Ganesh Colony", "Akashwani Chowk", "MIDC", "Khadka", "Pimprala", "Samta Nagar", "Navi Peth", "Old Jalgaon", "Shahunagar", "Tambapura", "Jilha Peth"], "Dhule": ["Deopur", "Agra Road", "Nakane Road", "Devpur", "Walwadi", "Mohadi", "Chalisgaon Road", "Sakri Road", "Fule Market", "Parola Road", "MIDC", "Avdhan", "Laling", "Shivaji Nagar", "Nagav"], "Ahilyanagar": ["Savedi", "Kedgaon", "Bhingar", "Nalegaon", "Maliwada", "Mukundnagar", "Pipeline Road", "Taraktpur", "Station Road", "Burudgaon Road", "Balikashram Road", "Premdan Chowk", "Delhi Gate", "Nagapur", "Bolhegaon"], "Sangli-Miraj-Kupwad": ["Sangli", "Miraj", "Kupwad", "Vishrambag", "Madhavnagar", "Wanlesswadi", "Gaon Bhag", "Dhamani Road", "Patrakar Nagar", "Sanjay Nagar", "Samta Nagar", "Kupwad MIDC", "Kavalapur", "Haripur", "Budhgaon"], "Malegaon": ["Camp", "Soygaon", "Islampura", "Sangameshwar", "Maliwada", "Naya Islampura", "Satana Road", "Mosam Pool", "Malegaon Camp", "Gandhi Nagar", "Sinnar Phata", "Pawarwadi", "Daregaon", "Kumbhar Tekdi", "Chandanpuri"], "Nanded-Waghala": ["Vazirabad", "Shivaji Nagar", "CIDCO", "Taroda", "Waghala", "Itwara", "Hyder Bagh", "Anand Nagar", "Asadullabad", "Kautha", "Airport Road", "Bafna", "Hanuman Peth", "Sangvi", "Degloor Naka"], "Latur": ["Ganj Golai", "Ausa Road", "Barshi Road", "Shivaji Nagar", "MIDC", "Vivekanand Chowk", "Nandi Stop", "Kawa Road", "Ring Road", "Rajiv Gandhi Chowk", "Moti Nagar", "Sawe Wadi", "Pakharsangvi", "Ambajogai Road", "Uday Nagar"], "Parbhani": ["Basmat Road", "Vasmat Road", "Station Road", "Jintur Road", "Gangakhed Road", "Karegaon Road", "Nanal Peth", "Khanapur", "Dargah Road", "Shivaji Nagar", "Mangalwar Bazar", "Old Mondha", "New Mondha", "Rahul Nagar", "Zari"], "Bhiwandi-Nizampur": ["Bhiwandi East", "Bhiwandi West", "Narpoli", "Kamatghar", "Dhamankar Naka", "Anjurphata", "Temghar", "Kalher", "Mankoli", "Khandupada", "Bhiwandi Station", "Shanti Nagar", "Fene Gaon", "Kongaon", "Purna"], "Mira-Bhayandar": ["Mira Road East", "Mira Road West", "Bhayandar East", "Bhayandar West", "Kashimira", "Kanakia", "Shanti Park", "Golden Nest", "Uttan", "Navghar", "Indralok", "Dahisar Check Naka", "Beverly Park", "Madhav Nagar", "Penkarpada"], "Kalyan-Dombivli": ["Kalyan West", "Kalyan East", "Dombivli East", "Dombivli West", "Thakurli", "Manpada", "Khadakpada", "Adharwadi", "Titwala", "Shahad", "Aayre", "Palava", "Gandhari", "Kolivali", "Manda"], "Ulhasnagar": ["Camp 1", "Camp 2", "Camp 3", "Camp 4", "Camp 5", "Shahad", "Vithalwadi", "Netaji Chowk", "Press Bazar", "Section 17", "Gol Maidan", "OT Section", "Khemani", "Ramnagar", "Bhatia Chowk"], "Vasai-Virar": ["Vasai West", "Vasai East", "Virar West", "Virar East", "Nalasopara West", "Nalasopara East", "Naigaon", "Bolinj", "Achole", "Evershine", "Manickpur", "Papdy", "Arnala", "Chandansar", "Pelhar"], "Panvel": ["Old Panvel", "New Panvel", "Kamothe", "Kalamboli", "Kharghar", "Taloja", "Roadpali", "Karanjade", "Palaspe", "Akurli", "Khanda Colony", "Navade", "Pushpak Nagar", "Jasai", "Ulwe"], "Ichalkaranji": ["Shahapur", "Kabnur", "Vikram Nagar", "Yadrav Road", "Ichalkaranji East", "Ichalkaranji West", "Jawaharnagar", "Rukmini Nagar", "Rendal Road", "Sangli Road", "Kolhapur Road", "Mane Nagar", "Gandhi Nagar", "Jaysingpur Road", "Hatkanangale Road"], "Jalna": ["Old Jalna", "New Jalna", "Mastgad", "Ambad Road", "Aurangabad Road", "Railway Station Area", "Moti Talab", "Mamta Nagar", "Samarth Nagar", "Shivaji Nagar", "Devalgaon Raja Road", "Daregaon", "Khadkeshwar", "Kacheri Road", "Mantha Road"], "Chandrapur": ["Civil Lines", "Bengali Camp", "Tukum", "Durgapur", "Urjanagar", "Bhadrawati Road", "Ballarpur Road", "Jatpura Gate", "Babupeth", "Pathanpura", "Ganj Ward", "Ram Nagar", "Padoli", "MIDC", "Lalpet"], "Pune": ["Aundh-Baner", "Shivajinagar", "Dhole Patil Road", "Yerawada-Dhanori", "Nagar Road", "Kothrud-Bavdhan", "Kasba Peth", "Bhavani Peth", "Wanowrie", "Hadapsar-Mundhwa", "Warje-Karvenagar", "Sinhagad Road", "Tilak Road", "Dhankawadi-Sahakarnagar", "Kondhwa-Yewalwadi"], "Nagpur": ["Mankapur", "Civil Lines", "Sadar", "Mahal", "Sitabuldi", "Trimurti Nagar", "Pratap Nagar", "Dhantoli", "Itwari", "Nandanvan", "Hingna", "Manish Nagar", "MIHAN", "Besa", "Wardhaman Nagar"]};
let currentCity="Pune";

function clamp(x){return Math.max(0,Math.min(1,x))}
function hei(l,c,v){return Math.round(100*(.45*clamp((l-37)/6)+.25*clamp(1-c/25)+.30*clamp(v/100)))}
function cat(h){return h>=70?["Critical","#b91c1c"]:h>=55?["High","#ea580c"]:h>=40?["Moderate","#ca8a04"]:["Lower","#15803d"]}
const L={hei:{n:"Heat Equity Index",f:w=>w.hei/100,u:"",a:"Lower",b:"Higher",hot:1},lst:{n:"Surface temp",f:w=>(w.lst-37)/6,u:"°C",a:"37°C",b:"43°C",hot:1},can:{n:"Tree canopy",f:w=>w.can/30,u:"%",a:"0%",b:"30%",hot:0},vul:{n:"Vulnerability",f:w=>w.vul/100,u:"",a:"Low",b:"High",hot:1}};
let layer="hei",sel=null;
const col=(t,hot)=>{t=clamp(t);if(!hot)t=1-t;return `hsl(${Math.round(58-58*t)} ${85}% ${Math.round(62-18*t)}%)`};
// Geographic-style map: ward territories = Voronoi cells of approximate ward centres, clipped to a city outline
const OUT=[[60,110],[110,40],[230,30],[360,35],[470,25],[560,70],[575,160],[560,260],[520,330],[450,395],[340,415],[220,410],[130,380],[75,300],[45,200]];
const SD=[[150,75],[265,140],[350,150],[440,75],[515,140],[105,175],[270,215],[335,235],[410,235],[510,260],[150,270],[205,350],[275,290],[320,360],[425,335]];
function clip(poly,a,b){const mx=(a[0]+b[0])/2,my=(a[1]+b[1])/2,nx=b[0]-a[0],ny=b[1]-a[1],d=p=>(p[0]-mx)*nx+(p[1]-my)*ny,o=[];
for(let i=0;i<poly.length;i++){const p=poly[i],q=poly[(i+1)%poly.length],dp=d(p),dq=d(q);if(dp<=0)o.push(p);if((dp<0&&dq>0)||(dp>0&&dq<0)){const t=dp/(dp-dq);o.push([p[0]+t*(q[0]-p[0]),p[1]+t*(q[1]-p[1])])}}return o}
function setGeometry(arr){
 arr.forEach((w,i)=>{let p=OUT;SD.forEach((q,j)=>{if(j!==i)p=clip(p,SD[i],q)});w.sx=SD[i][0];w.sy=SD[i][1];w.pts=p.map(v=>v.map(n=>n.toFixed(1)).join(",")).join(" ");w.cx=p.reduce((s,v)=>s+v[0],0)/p.length;w.cy=p.reduce((s,v)=>s+v[1],0)/p.length});
}
setGeometry(W);
const svg=document.getElementById("svg");let h=`<defs>
<filter id="rough" x="-5%" y="-5%" width="110%" height="110%"><feTurbulence type="fractalNoise" baseFrequency=".022" numOctaves="2" seed="7"/><feDisplacementMap in="SourceGraphic" scale="9"/></filter>
<filter id="tex"><feTurbulence type="fractalNoise" baseFrequency=".035" numOctaves="4" seed="3"/><feColorMatrix type="saturate" values="0"/></filter>
<clipPath id="cp"><polygon points="${OUT.map(v=>v.join(",")).join(" ")}"/></clipPath>
<pattern id="gr" width="30" height="30" patternUnits="userSpaceOnUse"><path d="M30 0H0V30" fill="none" stroke="var(--line)" stroke-width=".6"/></pattern></defs>
<rect width="600" height="440" fill="url(#gr)"/>
<polygon points="${OUT.map(v=>v.join(",")).join(" ")}" fill="none" stroke="var(--acc)" stroke-width="14" opacity=".12" stroke-linejoin="round"/>
<g filter="url(#rough)">`;
h+=W.map(w=>`<polygon class="ward" id="w${w.id}" tabindex="0" role="button" aria-label="${w.name} ward" points="${w.pts}" stroke-linejoin="round"><title>${w.name}</title></polygon>`).join("")+"</g>";
h+=`<g clip-path="url(#cp)" pointer-events="none">
<rect width="600" height="440" filter="url(#tex)" opacity=".32" style="mix-blend-mode:soft-light"/>
<ellipse cx="185" cy="158" rx="34" ry="16" fill="#3f7d20" opacity=".5" transform="rotate(-20 185 158)"/><ellipse cx="288" cy="258" rx="16" ry="11" fill="#3f7d20" opacity=".5"/><ellipse cx="205" cy="318" rx="26" ry="12" fill="#3f7d20" opacity=".4"/>
<g fill="none" stroke="#fff" stroke-opacity=".5" stroke-width="2.2" stroke-linecap="round"><path d="M50 120 C130 130 200 150 265 160 S360 175 420 130 560 70 575 65"/><path d="M270 215 C340 230 450 235 575 265"/><path d="M335 235 C320 300 300 360 300 415"/><path d="M265 140 C200 100 130 60 100 40"/><path d="M270 215 C215 260 160 330 120 385" stroke-dasharray="1 5"/><path d="M350 150 C400 100 440 60 470 20" stroke-dasharray="1 5"/></g>
<g fill="none" stroke-linecap="round"><path d="M45 145 C110 125 150 190 225 188 C275 184 300 168 335 172 C395 178 440 150 580 168" stroke="#0ea5e9" stroke-width="9" opacity=".85"/><path d="M45 145 C110 125 150 190 225 188 C275 184 300 168 335 172 C395 178 440 150 580 168" stroke="#bae6fd" stroke-width="3" opacity=".7"/>
<path d="M80 345 C130 305 175 250 228 192" stroke="#0ea5e9" stroke-width="6" opacity=".8"/></g>
<g font-family="Inter" font-size="8" font-style="italic" fill="#fff" opacity=".85"><text x="168" y="148">Vetal Tekdi</text><text x="274" y="248">Parvati</text><text x="470" y="62">✈ Airport</text><text x="95" y="157" fill="#e0f2fe">Mula</text><text x="395" y="190" fill="#e0f2fe">Mula–Mutha</text></g></g>`;
h+=W.map(w=>{const n=w.name.split("-");return `<text class="lbl" x="${w.cx}" y="${w.cy+(n.length>1?-1:4)}">${n.map((t,i)=>`<tspan x="${w.cx}" dy="${i?11:0}">${t}</tspan>`).join("")}</text>`}).join("");
h+='<g id="pins" pointer-events="none"></g><g font-family="Sora" fill="var(--mut)"><text x="570" y="24" font-size="11" text-anchor="end">N ↑</text><text x="14" y="430" font-size="10">${currentCity.toUpperCase()} · stylised map</text></g>';
svg.innerHTML=h;
W.forEach(w=>{const e=document.getElementById("w"+w.id);e.onclick=()=>pick(w.id);e.onkeydown=k=>{if(k.key==="Enter"||k.key===" "){k.preventDefault();pick(w.id)}}});
const tabs=document.getElementById("tabs");
Object.keys(L).forEach(k=>{const b=document.createElement("button");b.textContent=L[k].n;b.onclick=()=>{layer=k;paint()};b.dataset.k=k;tabs.appendChild(b)});
function paint(){const l=L[layer];W.forEach(w=>{const e=document.getElementById("w"+w.id);e.style.fill=col(l.f(w),l.hot);e.classList.toggle("sel",w.id===sel)});
[...tabs.children].forEach(b=>b.classList.toggle("on",b.dataset.k===layer));
document.getElementById("lbar").style.background=`linear-gradient(90deg,${col(0,l.hot)},${col(.5,l.hot)},${col(1,l.hot)})`;
document.getElementById("lmin").textContent=l.a;document.getElementById("lmax").textContent=l.b}
function bar(v,max,c){return `<div style="height:6px;border-radius:9px;background:var(--line);overflow:hidden"><i style="display:block;height:100%;width:${clamp(v/max)*100}%;background:${c}"></i></div>`}
function pick(id){sel=id;paint();const w=W[id],c=cat(w.hei);
const pn=w.loc.length;document.getElementById("pins").innerHTML=`<circle cx="${w.cx}" cy="${w.cy}" r="10" fill="none" stroke="var(--ink)" stroke-width="2"><animate attributeName="r" values="8;26;8" dur="2s" repeatCount="indefinite"/><animate attributeName="opacity" values=".9;0;.9" dur="2s" repeatCount="indefinite"/></circle>`+w.loc.map((x,i)=>{const t=-Math.PI/2+i*2*Math.PI/pn+.4,px=w.cx+Math.cos(t)*40,py=w.cy+Math.sin(t)*30+(w.cy<20?0:0);return `<circle cx="${px}" cy="${py}" r="3.5" fill="#fff" stroke="#111" stroke-width="1.5"/><text class="lbl2" x="${px}" y="${py-6}">${x}</text>`}).join("");
document.getElementById("panel").innerHTML=`<h3>${w.name}</h3><span class="badge" style="background:${c[1]}">${c[0]} priority · HEI ${w.hei}</span>
<div class="tiles"><div class="tile"><b>${w.lst.toFixed(1)}°C</b><small>Avg surface temp</small></div><div class="tile"><b>${w.can}%</b><small>Tree canopy</small></div><div class="tile"><b>${w.pop}k</b><small>Population</small></div><div class="tile"><b>${w.den}k/km²</b><small>Density</small></div></div>
<h4>Vulnerability</h4>${bar(w.vul,100,"#dc2626")}<h4>Canopy deficit</h4>${bar(25-Math.min(w.can,25),25,"#ea580c")}
<h4>Popular localities</h4><div class="chips">${w.loc.map(x=>`<span>${x}</span>`).join("")}</div>
<h4>Cooling what-if</h4><div class="sim"><label for="sl">Add tree canopy: <b id="sv">+0</b> pts</label><input type="range" id="sl" min="0" max="15" value="0">
<div id="so" style="font-size:14px;margin-top:4px"></div></div>`;
const sl=document.getElementById("sl");const f=()=>{const d=+sl.value,nl=w.lst-.12*d,nh=hei(nl,w.can+d,w.vul);document.getElementById("sv").textContent="+"+d;document.getElementById("so").innerHTML=`Projected temp <b>${nl.toFixed(1)}°C</b> (−${(.12*d).toFixed(1)}°) · HEI <b>${nh}</b> (${cat(nh)[0]})`};sl.oninput=f;f()}
// stats
const tp=W.reduce((s,w)=>s+w.pop,0),al=W.reduce((s,w)=>s+w.lst*w.pop,0)/tp,srt=[...W].sort((a,b)=>b.hei-a.hei);
const risk=W.filter(w=>w.hei>=55).reduce((s,w)=>s+w.pop,0);
document.getElementById("stats").innerHTML=[["15","PMC ward offices"],[al.toFixed(1)+"°C","Pop-weighted avg LST"],[(Math.max(...W.map(w=>w.lst))-Math.min(...W.map(w=>w.lst))).toFixed(1)+"°C","Hottest–coolest ward gap"],[Math.round(risk/tp*100)+"%","Residents in High/Critical wards"]].map(s=>`<div class="stat"><b>${s[0]}</b><small>${s[1]}</small></div>`).join("");
document.getElementById("ranklist").innerHTML=srt.map((w,i)=>`<button class="rk" data-i="${w.id}"><em>${i+1}</em><span class="n">${w.name}</span><span class="bar"><i style="width:${w.hei}%;background:${cat(w.hei)[1]}"></i></span><b>${w.hei}</b></button>`).join("");
document.querySelectorAll(".rk").forEach(b=>b.onclick=()=>{pick(+b.dataset.i);document.getElementById("map").scrollIntoView()});
document.getElementById("theme").onclick=()=>{const r=document.documentElement,d=r.dataset.theme?r.dataset.theme==="dark":matchMedia("(prefers-color-scheme:dark)").matches;r.dataset.theme=d?"light":"dark"};
paint();pick(srt[0].id);
const citySelect=document.getElementById("citySelect");
if(citySelect){
 citySelect.addEventListener("change",()=>{
   currentCity=citySelect.value;
   if(currentCity==="Nagpur") W=NAGPUR_W.map(w=>({...w,loc:[...w.loc]}));
   else if(currentCity==="Pune") W=PUNE_W.map(w=>({...w,loc:[...w.loc]}));
   else {
     const names=CITY_AREAS[currentCity]||CITY_AREAS.Pune;
     const base=PUNE_W;
     W=base.map((b,i)=>{const loc=names[i]||names[i%names.length];const next=names[(i+1)%names.length];const template={...b,id:i,name:(i%2===0?loc:loc+"–"+next),loc:[loc,next,names[(i+2)%names.length],names[(i+3)%names.length]]};
       // Keep the original map's visual structure; these are demo values, not measured city data.
       template.lst=+(b.lst+((i%3)-1)*0.4).toFixed(1);template.can=Math.max(4,Math.min(28,b.can+((i%4)-1)));template.pop=b.pop;template.den=b.den;template.vul=Math.max(25,Math.min(90,b.vul+((i%5)-2)*3));template.hei=hei(template.lst,template.can,template.vul);return template;});
   }
   W.forEach(w=>{w.hei=hei(w.lst,w.can,w.vul)}); setGeometry(W);
   sel=null;
   const nav=document.getElementById("mapNav"); if(nav) nav.textContent=currentCity+" Map";
   const mh=document.querySelector("#map .wrap h2"); if(mh) mh.textContent=currentCity+" neighbourhood heat explorer";
   const sub=document.querySelector("#map .wrap .sub"); if(sub) sub.textContent="Click any region to see its localities, heat exposure and equity score.";
   const label=document.querySelector("#map .card .note"); 
   // Rebuild SVG region polygons using the existing original-style renderer.
   rebuildMap();
 });
}
function rebuildMap(){
 const old=svg.innerHTML;
 // Refresh labels and ward polygons in the same original visual style using the same city-shaped map layout.
 let h=`<defs><filter id="rough" x="-5%" y="-5%" width="110%" height="110%"><feTurbulence type="fractalNoise" baseFrequency=".022" numOctaves="2" seed="7"/><feDisplacementMap in="SourceGraphic" scale="9"/></filter><filter id="tex"><feTurbulence type="fractalNoise" baseFrequency=".035" numOctaves="4" seed="3"/><feColorMatrix type="saturate" values="0"/></filter><clipPath id="cp"><polygon points="${OUT.map(v=>v.join(",")).join(" ")}"/></clipPath><pattern id="gr" width="30" height="30" patternUnits="userSpaceOnUse"><path d="M30 0H0V30" fill="none" stroke="var(--line)" stroke-width=".6"/></pattern></defs><rect width="600" height="440" fill="url(#gr)"/><polygon points="${OUT.map(v=>v.join(",")).join(" ")}" fill="none" stroke="var(--acc)" stroke-width="14" opacity=".12" stroke-linejoin="round"/><g filter="url(#rough)">`;
 h+=W.map(w=>`<polygon class="ward" id="w${w.id}" tabindex="0" role="button" aria-label="${w.name} region" points="${w.pts}" stroke-linejoin="round"><title>${w.name}</title></polygon>`).join("")+"</g>";
 h+=`<g clip-path="url(#cp)" pointer-events="none"><rect width="600" height="440" filter="url(#tex)" opacity=".32" style="mix-blend-mode:soft-light"/><ellipse cx="185" cy="158" rx="34" ry="16" fill="#3f7d20" opacity=".5" transform="rotate(-20 185 158)"/><ellipse cx="288" cy="258" rx="16" ry="11" fill="#3f7d20" opacity=".5"/><ellipse cx="205" cy="318" rx="26" ry="12" fill="#3f7d20" opacity=".4"/><g fill="none" stroke="#fff" stroke-opacity=".5" stroke-width="2.2" stroke-linecap="round"><path d="M50 120 C130 130 200 150 265 160 S360 175 420 130 560 70 575 65"/><path d="M270 215 C340 230 450 235 575 265"/><path d="M335 235 C320 300 300 360 300 415"/><path d="M265 140 C200 100 130 60 100 40"/><path d="M270 215 C215 260 160 330 120 385" stroke-dasharray="1 5"/></g><g fill="none" stroke-linecap="round"><path d="M45 145 C110 125 150 190 225 188 C275 184 300 168 335 172 C395 178 440 150 580 168" stroke="#0ea5e9" stroke-width="9" opacity=".85"/><path d="M45 145 C110 125 150 190 225 188 C275 184 300 168 335 172 C395 178 440 150 580 168" stroke="#bae6fd" stroke-width="3" opacity=".7"/></g><g font-family="Inter" font-size="8" font-style="italic" fill="#fff" opacity=".85"><text x="168" y="148">${currentCity==="Pune"?"Vetal Tekdi":"Gorewada"}</text><text x="274" y="248">${currentCity==="Pune"?"Parvati":"Futala"}</text><text x="470" y="62">${currentCity==="Pune"?"✈ Airport":"Nagpur Airport"}</text><text x="395" y="190">${currentCity==="Pune"?"Mula–Mutha":"Nag River"}</text></g></g>`;
 h+=W.map(w=>{const n=w.name.split(/[-–]/);return `<text class="lbl" x="${w.cx}" y="${w.cy+(n.length>1?-1:4)}">${n.map((t,i)=>`<tspan x="${w.cx}" dy="${i?11:0}">${t}</tspan>`).join("")}</text>`}).join("");
 h+='<g id="pins" pointer-events="none"></g><g font-family="Sora" fill="var(--mut)"><text x="570" y="24" font-size="11" text-anchor="end">N ↑</text><text x="14" y="430" font-size="10">'+currentCity.toUpperCase()+' · stylised map</text></g>';
 svg.innerHTML=h;
 W.forEach(w=>{const e=document.getElementById("w"+w.id);e.onclick=()=>pick(w.id);e.onkeydown=k=>{if(k.key==="Enter"||k.key===" "){k.preventDefault();pick(w.id)}}});
 const tabs=document.getElementById("tabs");[...tabs.children].forEach(b=>b.onclick=()=>{layer=b.dataset.k;paint()});
 document.getElementById("ranklist").innerHTML=[...W].sort((a,b)=>b.hei-a.hei).map((w,i)=>`<button class="rk" data-i="${w.id}"><em>${i+1}</em><span class="n">${w.name}</span><span class="bar"><i style="width:${w.hei}%;background:${cat(w.hei)[1]}"></i></span><b>${w.hei}</b></button>`).join("");
 document.querySelectorAll(".rk").forEach(b=>b.onclick=()=>{pick(+b.dataset.i);document.getElementById("map").scrollIntoView()});
 const tp=W.reduce((s,w)=>s+w.pop,0),al=W.reduce((s,w)=>s+w.lst*w.pop,0)/tp,srt=[...W].sort((a,b)=>b.hei-a.hei),risk=W.filter(w=>w.hei>=55).reduce((s,w)=>s+w.pop,0);
 document.getElementById("stats").innerHTML=[["15","neighbourhood regions"],[al.toFixed(1)+"°C","Pop-weighted avg sample LST"],[(Math.max(...W.map(w=>w.lst))-Math.min(...W.map(w=>w.lst))).toFixed(1)+"°C","Sample temperature gap"],[Math.round(risk/tp*100)+"%","Population in High/Critical sample regions"]].map(s=>`<div class="stat"><b>${s[0]}</b><small>${s[1]}</small></div>`).join("");
 paint();pick(srt[0].id);
}

</script></body></html>
