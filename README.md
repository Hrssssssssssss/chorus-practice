<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0">

<title>合唱祭 練習記録｜共同編集</title>

<style>
*{
  box-sizing:border-box;
}

body{
  margin:0;
  font-family:"Noto Sans JP","Yu Gothic",sans-serif;
  background:#f4f6fb;
  color:#222;
}

header{
  background:linear-gradient(135deg,#283593,#5c6bc0);
  color:#fff;
  padding:28px 20px;
  text-align:center;
  box-shadow:0 4px 15px #0002;
}

header h1{
  margin:0;
  font-size:30px;
}

header p{
  margin:8px 0 0;
  opacity:.92;
}

.container{
  width:min(1100px,94%);
  margin:30px auto 60px;
}

.card{
  background:#fff;
  border-radius:18px;
  padding:25px;
  margin-bottom:25px;
  box-shadow:0 5px 20px #00000012;
}

.card h2{
  margin-top:0;
  color:#283593;
  border-left:5px solid #5c6bc0;
  padding-left:12px;
}

.status{
  padding:10px 14px;
  border-radius:10px;
  background:#fff3cd;
  color:#795548;
  margin-bottom:18px;
}

.status.ok{
  background:#e8f5e9;
  color:#2e7d32;
}

.status.err{
  background:#ffebee;
  color:#c62828;
}

.form-grid{
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:18px;
}

.form-group{
  display:flex;
  flex-direction:column;
}

.full{
  grid-column:1/-1;
}

label{
  font-weight:bold;
  margin-bottom:7px;
}

input,
select,
textarea{
  width:100%;
  padding:12px 14px;
  border:1px solid #ccc;
  border-radius:10px;
  font-size:15px;
  font-family:inherit;
  outline:none;
}

input:focus,
select:focus,
textarea:focus{
  border-color:#5c6bc0;
  box-shadow:0 0 0 3px #5c6bc026;
}

textarea{
  min-height:110px;
  resize:vertical;
}

/* 星 */
.star-rating{
  display:flex;
  gap:5px;
  align-items:center;
}

.star{
  font-size:38px;
  color:#d5d5d5;
  cursor:pointer;
  transition:.15s;
  user-select:none;
}

.star:hover{
  transform:scale(1.15);
}

.star.active{
  color:#ffc107;
}

.rating-text{
  margin-left:10px;
  font-weight:bold;
  color:#555;
}

.buttons{
  display:flex;
  gap:12px;
  margin-top:22px;
  flex-wrap:wrap;
}

button{
  border:0;
  border-radius:10px;
  padding:12px 22px;
  font-size:15px;
  font-weight:bold;
  cursor:pointer;
  transition:.2s;
}

button:hover{
  transform:translateY(-2px);
  box-shadow:0 5px 12px #0002;
}

button:disabled{
  opacity:.6;
  cursor:not-allowed;
  transform:none;
}

.save-btn{
  background:#3949ab;
  color:#fff;
}

.clear-btn{
  background:#eee;
  color:#333;
}

.delete-all-btn,
.delete-btn{
  background:#e53935;
  color:#fff;
}

.search-area{
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:12px;
}

.record-count{
  color:#666;
  font-size:14px;
  margin-bottom:10px;
}

.record{
  border:1px solid #e0e0e0;
  border-radius:15px;
  padding:20px;
  margin-top:15px;
  background:#fafbff;
}

.record-header{
  display:flex;
  justify-content:space-between;
  align-items:flex-start;
  gap:15px;
  border-bottom:1px solid #ddd;
  padding-bottom:12px;
}

.record-title{
  font-size:21px;
  font-weight:bold;
  color:#283593;
}

.record-date{
  color:#666;
  font-size:14px;
}

.record-info{
  display:flex;
  flex-wrap:wrap;
  gap:10px;
  margin:15px 0;
}

.tag{
  background:#e8eaf6;
  color:#303f9f;
  padding:6px 10px;
  border-radius:20px;
  font-size:13px;
  font-weight:bold;
}

.record-section{
  margin-top:15px;
}

.record-section strong{
  display:block;
  margin-bottom:5px;
  color:#444;
}

.record-section p{
  white-space:pre-wrap;
  margin:0;
  line-height:1.7;
}

.record-stars{
  color:#ffc107;
  font-size:23px;
  letter-spacing:2px;
}

.empty{
  text-align:center;
  padding:40px 10px;
  color:#888;
}

.setup{
  background:#fff8e1;
  border:1px solid #ffe082;
  border-radius:12px;
  padding:15px;
  line-height:1.7;
}

.notice{
  background:#e8f0fe;
  border-radius:12px;
  padding:13px 15px;
  margin-top:12px;
  line-height:1.7;
}

code{
  background:#f1f1f1;
  padding:2px 5px;
  border-radius:5px;
}

.small{
  font-size:12px;
  color:#777;
  line-height:1.6;
}

@media(max-width:700px){

  header h1{
    font-size:24px;
  }

  .form-grid,
  .search-area{
    grid-template-columns:1fr;
  }

  .full{
    grid-column:auto;
  }

  .card{
    padding:18px;
  }

  .record-header{
    flex-direction:column;
  }

  .star{
    font-size:34px;
  }

}
</style>
</head>

<body>

<header>

<h1>🎶 合唱祭 練習記録</h1>

<p>
みんなで共有・共同編集できる練習記録
</p>

</header>


<div class="container">


<!-- 接続状態 -->

<div id="status" class="status">
接続準備中...
</div>


<!-- 設定説明 -->

<div class="card">

<h2>⚙️ Googleスプレッドシート接続</h2>

<div class="setup">

このサイトは
<b>Googleスプレッドシート</b>
を使ってみんなで同じ練習記録を共有します。

<br><br>

下のJavaScriptにある

<code>API_URL</code>

に、Google Apps ScriptのウェブアプリURLを設定してください。

<div class="notice">

<strong>ポイント</strong><br>

Googleスプレッドシートを全員に編集共有する必要はありません。<br>

このサイトから同じスプレッドシートへ記録を保存します。

</div>

</div>

</div>



<!-- 記録入力 -->

<div class="card">

<h2>📝 練習を記録</h2>


<div class="form-grid">


<div class="form-group">

<label>📅 練習日</label>

<input
type="date"
id="date"
>

</div>



<div class="form-group">

<label>🎵 曲名</label>

<input
type="text"
id="song"
placeholder="例：COSMOS"
>

</div>



<div class="form-group">

<label>⏱️ 練習時間</label>

<select id="time">

<option value="">
選択してください
</option>

<option>15分</option>
<option>30分</option>
<option>45分</option>
<option>1時間</option>
<option>1時間30分</option>
<option>2時間</option>
<option>2時間以上</option>

</select>

</div>



<div class="form-group">

<label>👥 参加人数</label>

<input
type="number"
id="people"
min="0"
placeholder="例：35"
>

</div>



<!-- 星評価 -->

<div class="form-group full">

<label>
⭐ 今日の練習評価
</label>


<div
class="star-rating"
id="starRating"
>

<span
class="star"
data-value="1"
>★</span>

<span
class="star"
data-value="2"
>★</span>

<span
class="star"
data-value="3"
>★</span>

<span
class="star"
data-value="4"
>★</span>

<span
class="star"
data-value="5"
>★</span>

<span
class="rating-text"
id="ratingText"
>
未評価
</span>

</div>

</div>



<!-- 練習内容 -->

<div class="form-group full">

<label>
📝 練習内容
</label>

<textarea
id="practice"
placeholder="例：
・発声練習
・1番を重点的に練習
・アルトの音程を確認"
></textarea>

</div>



<!-- メモ -->

<div class="form-group full">

<label>
💬 反省・メモ
</label>

<textarea
id="memo"
placeholder="今日できなかったこと、次回頑張ることなど"
></textarea>

</div>


</div>


<div class="buttons">

<button
class="save-btn"
id="saveBtn"
>
💾 みんなに共有して保存
</button>

<button
class="clear-btn"
id="clearBtn"
>
🔄 入力をクリア
</button>

</div>

</div>



<!-- 検索 -->

<div class="card">

<h2>
🔍 練習記録を検索
</h2>


<div class="search-area">


<div>

<label>
📅 日付
</label>

<input
type="date"
id="searchDate"
>

</div>



<div>

<label>
🎵 曲名
</label>

<input
type="text"
id="searchSong"
placeholder="曲名を入力"
>

</div>


</div>


<div class="buttons">

<button
class="clear-btn"
id="clearSearchBtn"
>
🔄 検索をリセット
</button>

</div>

</div>



<!-- 記録一覧 -->

<div class="card">

<h2>
📋 みんなの練習記録
</h2>


<div
class="record-count"
id="recordCount"
>
0件の記録
</div>


<div id="recordList">

<div class="empty">
📡 データを読み込んでいます...
</div>

</div>


<div class="buttons">

<button
class="delete-all-btn"
id="deleteAllBtn"
>
🗑️ すべて削除（パスワード必要）
</button>

</div>


<p class="small">

※削除パスワードはGoogle Apps Script側で確認されます。

</p>

</div>


</div>



<!--
==================================================
Google Apps Scriptへ送るための隠しフォーム
==================================================
-->

<iframe
name="postFrame"
id="postFrame"
style="display:none"
></iframe>


<form
id="postForm"
method="POST"
target="postFrame"
style="display:none"
>

<input name="action" id="postAction">

<input name="date" id="postDate">

<input name="song" id="postSong">

<input name="time" id="postTime">

<input name="people" id="postPeople">

<input name="rating" id="postRating">

<textarea name="practice" id="postPractice"></textarea>

<textarea name="memo" id="postMemo"></textarea>

<input name="id" id="postId">

<input name="password" id="postPassword">

</form>



<script>


/*
=========================================================
★★★ ここを変更 ★★★

Google Apps ScriptをウェブアプリとしてデプロイしたURL

例：

const API_URL =
"https://script.google.com/macros/s/AKfycbzfo1DG6zmf3nVWp-dowloj5e_gQgZyiz7PmgejgWVVwNha7MUIeH9H7_T-LbrsMKp-/exec";

=========================================================
*/

const API_URL =
"https://script.google.com/macros/s/AKfycbzfo1DG6zmf3nVWp-dowloj5e_gQgZyiz7PmgejgWVVwNha7MUIeH9H7_T-LbrsMKp-/exec";



let selectedRating = 0;

let allRecords = [];

let loading = false;



const statusEl =
document.getElementById("status");



/*
=========================================================
ステータス
=========================================================
*/

function setStatus(
text,
type=""
){

statusEl.textContent = text;

statusEl.className =
"status " + type;

}



/*
=========================================================
今日の日付
=========================================================
*/

function pad(n){

return String(n).padStart(2,"0");

}


function setToday(){

const d = new Date();

document.getElementById("date").value =

`${d.getFullYear()}-${pad(d.getMonth()+1)}-${pad(d.getDate())}`;

}


setToday();



/*
=========================================================
星評価
=========================================================
*/

const stars =
document.querySelectorAll(".star");


stars.forEach(star=>{

star.addEventListener(
"click",
()=>{

selectedRating =
Number(star.dataset.value);


stars.forEach(s=>{

s.classList.toggle(
"active",
Number(s.dataset.value)
<= selectedRating
);

});


document.getElementById(
"ratingText"
).textContent =
`${selectedRating} / 5`;

}
);

});



/*
=========================================================
入力クリア
=========================================================
*/

function clearForm(){

document.getElementById(
"song"
).value="";


document.getElementById(
"time"
).value="";


document.getElementById(
"people"
).value="";


document.getElementById(
"practice"
).value="";


document.getElementById(
"memo"
).value="";


selectedRating=0;


stars.forEach(
s=>s.classList.remove("active")
);


document.getElementById(
"ratingText"
).textContent="未評価";


setToday();

}


document.getElementById(
"clearBtn"
).onclick=clearForm;



/*
=========================================================
HTMLエスケープ
=========================================================
*/

function escapeHTML(text){

const div =
document.createElement("div");

div.textContent =
text ?? "";

return div.innerHTML;

}



/*
=========================================================
日付表示
=========================================================
*/

function formatDate(s){

if(!s) return "";

const [
y,
m,
d
] =
String(s).split("-");

return `${y}年${Number(m)}月${Number(d)}日`;

}



/*
=========================================================
検索
=========================================================
*/

function filteredRecords(){

const date =
document.getElementById(
"searchDate"
).value;


const song =
document.getElementById(
"searchSong"
).value
.trim()
.toLowerCase();


return allRecords.filter(r =>

(!date ||
r.date === date)

&&

(!song ||
String(r.song || "")
.toLowerCase()
.includes(song))

);

}



/*
=========================================================
記録表示
=========================================================
*/

function render(){

const records =
filteredRecords()
.sort((a,b)=>{

const da =
a.date || "";

const db =
b.date || "";


if(da !== db){

return db.localeCompare(da);

}


return
(Number(b.createdAtMs)||0)
-
(Number(a.createdAtMs)||0);

});


document.getElementById(
"recordCount"
).textContent =
`${records.length}件の記録`;


const list =
document.getElementById(
"recordList"
);


if(!records.length){

list.innerHTML =
'<div class="empty">📭 該当する練習記録はありません</div>';

return;

}


list.innerHTML="";


records.forEach(r=>{


let starsHTML="";


for(
let i=1;
i<=5;
i++
){

starsHTML +=
i <= Number(r.rating)
? "★"
: "☆";

}



const div =
document.createElement("div");


div.className="record";


div.innerHTML=`

<div class="record-header">

<div>

<div class="record-title">

🎵 ${escapeHTML(r.song)}

</div>


<div class="record-date">

📅 ${formatDate(r.date)}

</div>

</div>


<button
class="delete-btn"
data-id="${escapeHTML(r.id)}"
>

🗑️ 削除

</button>

</div>



<div class="record-info">

${r.time
? `<span class="tag">
⏱️ ${escapeHTML(r.time)}
</span>`
: ""}


${r.people !== ""
&& r.people != null

? `<span class="tag">
👥 ${escapeHTML(String(r.people))}人
</span>`

: ""}


<span class="tag">

⭐ ${Number(r.rating)||0}/5

</span>

</div>



<div class="record-section">

<strong>
⭐ 評価
</strong>

<div class="record-stars">

${starsHTML}

</div>

</div>



${r.practice

? `<div class="record-section">

<strong>
📝 練習内容
</strong>

<p>
${escapeHTML(r.practice)}
</p>

</div>`

: ""}



${r.memo

? `<div class="record-section">

<strong>
💬 反省・メモ
</strong>

<p>
${escapeHTML(r.memo)}
</p>

</div>`

: ""}

`;


div.querySelector(
".delete-btn"
).onclick =
()=>deleteOne(r.id);


list.appendChild(div);

});

}



/*
=========================================================
Googleスプレッドシートから読み込み
=========================================================
*/

function loadRecords(){

if(
API_URL.startsWith("ここに")
){

setStatus(
"⚠️ API_URLがまだ設定されていません。",
"err"
);


document.getElementById(
"recordList"
).innerHTML =

'<div class="empty">⚙️ Google Apps ScriptのURLを設定してください</div>';

return;

}



const callback =
"jsonp_"
+ Date.now()
+ "_"
+ Math.floor(
Math.random()*100000
);


const script =
document.createElement("script");


let finished=false;



window[callback] =
(result)=>{

finished=true;


delete window[callback];

script.remove();



if(
result &&
result.ok
){

allRecords =
Array.isArray(
result.records
)
? result.records
: [];


render();


setStatus(
"🟢 オンライン｜みんなの変更を自動更新中",
"ok"
);

}

else{

setStatus(
"🔴 データ取得に失敗しました。",
"err"
);

}

};



script.onerror=()=>{

if(finished) return;

finished=true;

delete window[callback];

script.remove();


setStatus(
"🔴 Googleスプレッドシートに接続できません。",
"err"
);

};



script.src =
API_URL
+ "?action=list"
+ "&callback="
+ encodeURIComponent(callback)
+ "&_="
+ Date.now();


document.body.appendChild(script);

}



/*
=========================================================
POST
=========================================================
*/

function post(data){

const form =
document.getElementById(
"postForm"
);


form.action =
API_URL;


Object.keys(data)
.forEach(k=>{

const id =
"post"
+
k.charAt(0).toUpperCase()
+
k.slice(1);


const el =
document.getElementById(id);


if(el){

el.value =
data[k] ?? "";

}

});


form.submit();

}



/*
=========================================================
保存
=========================================================
*/

document.getElementById(
"saveBtn"
).onclick=()=>{


if(loading) return;



const data={

date:
document.getElementById(
"date"
).value,


song:
document.getElementById(
"song"
).value.trim(),


time:
document.getElementById(
"time"
).value,


people:
document.getElementById(
"people"
).value,


rating:
selectedRating,


practice:
document.getElementById(
"practice"
).value.trim(),


memo:
document.getElementById(
"memo"
).value.trim()

};



if(!data.date){

alert(
"練習日を入力してください。"
);

return;

}



if(!data.song){

alert(
"曲名を入力してください。"
);

return;

}



if(!data.rating){

alert(
"星評価を選択してください。"
);

return;

}



loading=true;


document.getElementById(
"saveBtn"
).disabled=true;


setStatus(
"💾 保存しています..."
);



post({

action:"save",

...data

});



setTimeout(()=>{

loading=false;

document.getElementById(
"saveBtn"
).disabled=false;

loadRecords();

},1500);



clearForm();


alert(
"練習記録を共有しました！🎉\n\nみんなの画面にも反映されます。"
);

};



/*
=========================================================
1件削除
=========================================================
*/

function deleteOne(id){

const pass =
prompt(
"削除パスワードを入力してください"
);


if(pass===null) return;


if(!pass){

alert(
"パスワードを入力してください。"
);

return;

}



if(
!confirm(
"この記録を削除しますか？"
)
){

return;

}



setStatus(
"🗑️ 削除しています..."
);


post({

action:"delete",

id:id,

password:pass

});


setTimeout(
loadRecords,
1500
);

}



/*
=========================================================
全部削除
=========================================================
*/

document.getElementById(
"deleteAllBtn"
).onclick=()=>{


const pass =
prompt(
"すべて削除するためのパスワードを入力してください"
);


if(pass===null) return;


if(!pass){

alert(
"パスワードを入力してください。"
);

return;

}



if(
!confirm(
"本当にすべての記録を削除しますか？\n\nこの操作は元に戻せません。"
)
){

return;

}



setStatus(
"🗑️ すべて削除しています..."
);


post({

action:"deleteAll",

password:pass

});


setTimeout(
loadRecords,
1500
);

};



/*
=========================================================
検索
=========================================================
*/

document.getElementById(
"searchDate"
).oninput=render;


document.getElementById(
"searchSong"
).oninput=render;



document.getElementById(
"clearSearchBtn"
).onclick=()=>{

document.getElementById(
"searchDate"
).value="";


document.getElementById(
"searchSong"
).value="";


render();

};



/*
=========================================================
5秒ごとに自動更新
=========================================================
*/

setInterval(
loadRecords,
5000
);



/*
=========================================================
最初に読み込み
=========================================================
*/

loadRecords();


</script>

</body>
</html>
