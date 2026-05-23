<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Walk With Yeshua — Luke Chapter 2</title>
<link href="https://fonts.googleapis.com/css2?family=Fredoka+One&family=Nunito:wght@400;600;700;800&display=swap" rel="stylesheet">
<style>
* { box-sizing: border-box; margin: 0; padding: 0; }
body {
  font-family: 'Nunito', sans-serif;
  background: #0d0d2b;
  min-height: 100vh;
  display: flex;
  align-items: flex-start;
  justify-content: center;
  padding: 24px 16px 48px;
}
#game-wrap {
  width: 100%;
  max-width: 640px;
  background: linear-gradient(180deg, #1a1a3e 0%, #2d1b5e 50%, #1e3a5f 100%);
  border-radius: 20px;
  overflow: hidden;
  position: relative;
  box-shadow: 0 24px 80px rgba(0,0,0,0.6);
}
.stars-bg { position: absolute; top:0; left:0; width:100%; height:100%; pointer-events:none; overflow:hidden; }
.star-dot { position:absolute; background:#fff; border-radius:50%; animation:twinkle 2s infinite alternate; }
@keyframes twinkle { from{opacity:0.3} to{opacity:1} }
.screen { display:none; padding:28px 28px 36px; position:relative; z-index:2; animation:fadeIn 0.5s ease; }
.screen.active { display:block; }
@keyframes fadeIn { from{opacity:0;transform:translateY(12px)} to{opacity:1;transform:translateY(0)} }
.title-area { text-align:center; padding:28px 12px 20px; }
.game-title { font-family:'Fredoka One',cursive; font-size:42px; color:#f5c842; text-shadow:0 0 40px rgba(245,200,66,0.35); line-height:1.1; margin-bottom:8px; }
.game-subtitle { font-size:14px; color:#c4b5fd; font-weight:700; letter-spacing:0.08em; text-transform:uppercase; }
.scene-art { font-size:58px; text-align:center; margin-bottom:12px; line-height:1; }
.intro-card { background:rgba(255,255,255,0.07); border:1px solid rgba(245,200,66,0.25); border-radius:16px; padding:20px 22px; margin-bottom:20px; color:#f0e6d3; font-size:15px; line-height:1.8; }
.intro-card .card-heading { font-size:16px; font-weight:800; color:#fde68a; text-align:center; margin-bottom:8px; }
.stars-row { display:flex; justify-content:center; gap:10px; margin:16px 0 22px; font-size:30px; }
.star-item { opacity:0.2; transition:all 0.4s; }
.star-item.earned { opacity:1; animation:popIn 0.4s ease; }
@keyframes popIn { 0%{transform:scale(0)} 70%{transform:scale(1.3)} 100%{transform:scale(1)} }
.start-btn { display:block; margin:0 auto; background:linear-gradient(135deg,#f5c842 0%,#f59e0b 100%); border:none; border-radius:28px; padding:18px 52px; color:#1a1a3e; font-size:22px; font-weight:800; font-family:'Fredoka One',cursive; cursor:pointer; transition:all 0.25s; letter-spacing:0.02em; box-shadow:0 6px 28px rgba(245,200,66,0.3); }
.start-btn:hover { transform:scale(1.05); box-shadow:0 10px 36px rgba(245,200,66,0.45); }
.step-row { display:flex; justify-content:space-between; color:rgba(196,181,253,0.75); font-size:12px; font-weight:700; margin-bottom:8px; letter-spacing:0.06em; text-transform:uppercase; }
.progress-wrap { background:rgba(255,255,255,0.1); border-radius:8px; height:8px; margin-bottom:22px; overflow:hidden; }
.progress-fill { height:100%; background:linear-gradient(90deg,#f5c842,#4ade80); border-radius:8px; transition:width 0.6s ease; }
.scene-header { display:flex; align-items:center; gap:12px; margin-bottom:16px; }
.scene-icon { font-size:38px; line-height:1; }
.scene-title { font-family:'Fredoka One',cursive; font-size:24px; color:#f5c842; line-height:1.1; }
.verse-tag { display:inline-block; background:rgba(245,200,66,0.15); color:#fde68a; font-size:11px; font-weight:800; padding:3px 10px; border-radius:20px; letter-spacing:0.06em; margin-top:3px; }
.story-card { background:rgba(255,255,255,0.07); border:1px solid rgba(245,200,66,0.2); border-radius:16px; padding:18px 22px; margin-bottom:18px; color:#f0e6d3; font-size:15px; line-height:1.85; }
.question-box { background:rgba(255,251,235,0.08); border:1.5px solid rgba(245,200,66,0.4); border-radius:14px; padding:16px 20px; margin-bottom:18px; color:#fde68a; font-size:16px; font-weight:700; text-align:center; line-height:1.5; }
.choices { display:grid; grid-template-columns:1fr 1fr; gap:12px; margin-bottom:18px; }
@media(max-width:480px){ .choices{grid-template-columns:1fr} }
.choice-btn { background:rgba(255,255,255,0.07); border:1.5px solid rgba(196,181,253,0.3); border-radius:14px; padding:14px 12px; color:#e9d5ff; font-size:14px; font-weight:600; font-family:'Nunito',sans-serif; cursor:pointer; transition:all 0.2s; line-height:1.45; text-align:center; }
.choice-btn:hover:not(:disabled) { background:rgba(245,200,66,0.15); border-color:#f5c842; color:#fde68a; transform:translateY(-2px); }
.choice-btn.correct { background:rgba(74,222,128,0.2); border-color:#4ade80; color:#bbf7d0; }
.choice-btn.wrong { background:rgba(248,113,113,0.2); border-color:#f87171; color:#fecaca; }
.choice-btn:disabled { cursor:default; transform:none !important; }
.feedback { display:none; border-radius:14px; padding:16px 20px; margin-bottom:18px; font-size:15px; line-height:1.65; font-weight:600; }
.feedback.show { display:block; animation:fadeIn 0.4s ease; }
.feedback.good { background:rgba(74,222,128,0.12); border:1px solid rgba(74,222,128,0.35); color:#d1fae5; }
.feedback.try-again { background:rgba(251,191,36,0.1); border:1px solid rgba(251,191,36,0.35); color:#fef3c7; }
.feedback-emoji { font-size:20px; margin-bottom:6px; display:block; }
.truth-badge { background:linear-gradient(135deg,rgba(245,200,66,0.15),rgba(196,181,253,0.15)); border:1px solid rgba(245,200,66,0.45); border-radius:12px; padding:12px 16px; margin-top:14px; color:#fde68a; font-size:13px; font-weight:700; line-height:1.5; }
.truth-badge .badge-label { font-size:10px; letter-spacing:0.18em; text-transform:uppercase; color:#c4b5fd; font-weight:800; display:block; margin-bottom:5px; }
.next-btn { display:block; width:100%; background:linear-gradient(135deg,#f5c842 0%,#f59e0b 100%); border:none; border-radius:14px; padding:16px; color:#1a1a3e; font-size:18px; font-weight:800; font-family:'Nunito',sans-serif; cursor:pointer; transition:all 0.2s; letter-spacing:0.02em; }
.next-btn:hover { transform:translateY(-2px); box-shadow:0 6px 24px rgba(245,200,66,0.35); }
.final-heading { text-align:center; margin-bottom:20px; }
.final-heading h1 { font-family:'Fredoka One',cursive; font-size:32px; color:#f5c842; margin-bottom:4px; }
.final-heading p { font-size:13px; color:#c4b5fd; font-weight:700; letter-spacing:0.07em; text-transform:uppercase; }
.score-circle { width:128px; height:128px; border-radius:50%; background:linear-gradient(135deg,#f5c842,#f59e0b); display:flex; flex-direction:column; align-items:center; justify-content:center; margin:0 auto 16px; box-shadow:0 8px 32px rgba(245,200,66,0.35); }
.score-num { font-family:'Fredoka One',cursive; font-size:46px; color:#1a1a3e; line-height:1; }
.score-denom { font-size:12px; font-weight:800; color:#78350f; letter-spacing:0.04em; }
.score-message { text-align:center; color:#fde68a; font-size:17px; font-weight:700; margin-bottom:22px; line-height:1.5; padding:0 8px; }
.truths-card { background:rgba(255,255,255,0.07); border:1px solid rgba(245,200,66,0.2); border-radius:16px; padding:18px 22px; margin-bottom:16px; }
.truths-heading { font-size:10px; letter-spacing:0.2em; text-transform:uppercase; color:#c4b5fd; font-weight:800; text-align:center; margin-bottom:14px; }
.truth-line { border-left:3px solid #f5c842; padding:8px 14px; margin-bottom:10px; color:#fde68a; font-size:14px; font-weight:600; line-height:1.55; }
.truth-line:last-child { margin-bottom:0; }
.verse-card { background:rgba(255,255,255,0.07); border:1px solid rgba(245,200,66,0.2); border-radius:16px; padding:18px 22px; margin-bottom:22px; text-align:center; }
.verse-card .ref { font-family:'Fredoka One',cursive; font-size:18px; color:#f5c842; margin-bottom:8px; }
.verse-card .verse-text { color:#f0e6d3; font-size:15px; line-height:1.8; font-style:italic; }
.verse-card .verse-note { color:#c4b5fd; font-size:13px; margin-top:10px; font-weight:600; }
.replay-btn { display:block; width:100%; background:linear-gradient(135deg,#f5c842 0%,#f59e0b 100%); border:none; border-radius:14px; padding:16px; color:#1a1a3e; font-size:18px; font-weight:800; font-family:'Nunito',sans-serif; cursor:pointer; transition:all 0.2s; }
.replay-btn:hover { transform:translateY(-2px); box-shadow:0 6px 24px rgba(245,200,66,0.35); }
</style>
</head>
<body>
<div id="game-wrap">
  <div class="stars-bg" id="stars"></div>

  <div id="screen-home" class="screen active">
    <div class="title-area">
      <div class="scene-art">✨🌟✨</div>
      <div class="game-title">Walk With Yeshua</div>
      <div class="game-subtitle">A Journey Through Luke Chapter 2</div>
    </div>
    <div class="intro-card">
      <div class="card-heading">For Young Followers of God</div>
      Follow Yeshua through five exciting adventures — from his birth in Bethlehem, to the Temple in Jerusalem. Learn what it truly means to be a child of God! 🌿
    </div>
    <div class="stars-row">
      <span class="star-item">⭐</span>
      <span class="star-item">⭐</span>
      <span class="star-item">⭐</span>
      <span class="star-item">⭐</span>
      <span class="star-item">⭐</span>
    </div>
    <button class="start-btn" onclick="startGame()">Begin the Journey</button>
  </div>

  <div id="screen-story" class="screen"></div>
  <div id="screen-final" class="screen"></div>
</div>

<script>
const STORIES = [
  {
    title:"The Humble Beginning", icon:"🐑", verseRef:"Luke 2:6–7",
    narrative:"Mary and Joseph had traveled a very long way to the city of Bethlehem. When they arrived, there was <strong style='color:#fde68a'>no room</strong> for them in the inn. So Yeshua was born in a simple stable, wrapped in cloths, and laid in a manger — a feeding box for animals. The Son of God entered the world not in a palace, but in the humblest of places.",
    question:"Yeshua, the Son of God, was born in a humble stable. What does this teach us about God?",
    choices:[
      {text:"God loves rich and powerful people most",correct:false},
      {text:"God comes close to us in simple, humble places",correct:true},
      {text:"God only lives in big, fancy temples",correct:false},
      {text:"God does not care where we are",correct:false}
    ],
    goodFeedback:"Yes! Yeshua did not come in a palace — he came humbly. God meets us wherever we are, even in the simple, ordinary moments of life. Being a child of God means staying humble and kind, just like Yeshua.",
    tryFeedback:"Think again! Yeshua was born in a stable, not a palace. God chose the simplest place on purpose to show us something beautiful about His heart.",
    truth:"A child of God stays humble — no place or person is too small for God's love."
  },
  {
    title:"The Shepherds Listen", icon:"🌙", verseRef:"Luke 2:8–20",
    narrative:"Out in the fields near Bethlehem, <strong style='color:#fde68a'>shepherds</strong> were watching over their flocks at night. Suddenly, an angel of the Lord appeared and the glory of God shone around them! The angel said: <em style='color:#c4b5fd'>\"Do not be afraid! I bring you good news of great joy for all people.\"</em> The shepherds went right away to find Yeshua — and what they found changed everything.",
    question:"The shepherds heard the good news and went quickly. What did they do after they saw Yeshua?",
    choices:[
      {text:"They kept it secret and told nobody",correct:false},
      {text:"They went back to sleep in the fields",correct:false},
      {text:"They shared the good news with everyone they met",correct:true},
      {text:"They asked for a reward from God",correct:false}
    ],
    goodFeedback:"Amazing! The shepherds were so full of joy that they told everyone what they had heard and seen. Luke 2:17 says they \"spread the word.\" A child of God shares good news — not because they have to, but because their heart is overflowing with joy!",
    tryFeedback:"Look at Luke 2:17! After the shepherds saw Yeshua, they went and told everyone. They couldn't keep the good news to themselves. Try again!",
    truth:"A child of God shares joy and good news with others — freely and gladly."
  },
  {
    title:"Mary Pondered in Her Heart", icon:"💫", verseRef:"Luke 2:19",
    narrative:"After the shepherds came and shared everything the angel had told them, the people who heard it were amazed! But Mary — Yeshua's mother — did something very different. The scripture says: <em style='color:#c4b5fd'>\"Mary treasured up all these things and pondered them in her heart.\"</em> In the middle of all the excitement, she grew very still and held God's words close.",
    question:"Mary quietly treasured God's words in her heart. What can we learn from her example?",
    choices:[
      {text:"We should only think about fun things, not God",correct:false},
      {text:"We should take time to think quietly about what God does and says",correct:true},
      {text:"It is wrong to feel amazed by God",correct:false},
      {text:"We should forget what God tells us quickly",correct:false}
    ],
    goodFeedback:"Beautiful! Mary shows us that being close to God is not always about talking. Sometimes it means sitting quietly and thinking deeply about what God has done. A child of God treasures God's word — keeping it safe in their heart like a precious gift.",
    tryFeedback:"Mary's secret was her quiet heart. She didn't rush past what God was doing — she slowed down and treasured it. Try again!",
    truth:"A child of God keeps quiet time with God — treasuring His words deep in their heart."
  },
  {
    title:"Presented Before God", icon:"🕊️", verseRef:"Luke 2:22–38",
    narrative:"When Yeshua was a baby, Mary and Joseph brought him to the Temple in Jerusalem to present him before God. A faithful old man named <strong style='color:#fde68a'>Simeon</strong> had been waiting his whole life to see God's promised one. When he finally held baby Yeshua in his arms, he praised God with great joy! He recognized God's work — in a tiny baby, in an ordinary moment.",
    question:"Simeon praised God the moment he saw Yeshua. What does Simeon's joyful praise teach us?",
    choices:[
      {text:"We should only praise God when everything goes our way",correct:false},
      {text:"Praising God is not important for children",correct:false},
      {text:"We can recognize and praise God even in surprising places",correct:true},
      {text:"God does not want us to speak to Him",correct:false}
    ],
    goodFeedback:"Wonderful! Simeon recognized God's work even in a tiny baby in the Temple! He didn't wait for something big and flashy. A child of God has eyes open to see God at work all around — and a heart ready to give thanks!",
    tryFeedback:"Simeon saw God's promise in the most unexpected place — a small baby held in his arms. He praised God right then and there! What does that teach us about praise?",
    truth:"A child of God keeps their eyes open for God — and praises Him with a grateful heart."
  },
  {
    title:"Growing in Wisdom", icon:"📜", verseRef:"Luke 2:41–52",
    narrative:"When Yeshua was twelve years old, his family went to Jerusalem for the Passover feast. On the way home, they couldn't find him! After three days of searching, they found him <strong style='color:#fde68a'>in the Temple</strong>, sitting among the teachers — listening carefully and asking questions. Everyone was amazed at his understanding. Yeshua told his parents: <em style='color:#c4b5fd'>\"I must be in my Father's house.\"</em>",
    question:"Young Yeshua was in the Temple — listening and asking questions. What does this show us about growing close to God?",
    choices:[
      {text:"Smart children don't need to ask questions about God",correct:false},
      {text:"We grow closer to God by listening, learning, and asking with a hungry heart",correct:true},
      {text:"Only grown-ups are allowed to learn about God",correct:false},
      {text:"Being in God's house is not important for young people",correct:false}
    ],
    goodFeedback:"Yes! Even at twelve, Yeshua was hungry to know and understand his Father. He listened carefully and asked real questions. Luke 2:52 says he \"grew in wisdom and stature, and in favor with God and people.\" That is the goal for every child of God!",
    tryFeedback:"Yeshua — the very Son of God — still sat and listened and asked questions! Growing in God's wisdom is a lifelong journey, even for the youngest hearts.",
    truth:"A child of God never stops learning — listening, asking, and growing in God's wisdom every day."
  }
];

let current=0,score=0,truths=[],answered=false;

const starsEl=document.getElementById('stars');
for(let i=0;i<70;i++){
  const s=document.createElement('div');
  s.className='star-dot';
  const sz=Math.random()*2.5+0.5;
  s.style.cssText=`left:${Math.random()*100}%;top:${Math.random()*100}%;width:${sz}px;height:${sz}px;animation-delay:${Math.random()*3}s;animation-duration:${1.5+Math.random()*2}s`;
  starsEl.appendChild(s);
}

function startGame(){ current=0;score=0;truths=[];showStory(0); }

function showStory(idx){
  answered=false;
  const s=STORIES[idx];
  const pct=Math.round((idx/STORIES.length)*100);
  const el=document.getElementById('screen-story');
  el.innerHTML=`
    <div class="step-row"><span>Scene ${idx+1} of ${STORIES.length}</span><span>${score} ⭐ earned</span></div>
    <div class="progress-wrap"><div class="progress-fill" style="width:${pct}%"></div></div>
    <div class="scene-header">
      <div class="scene-icon">${s.icon}</div>
      <div><div class="scene-title">${s.title}</div><span class="verse-tag">${s.verseRef}</span></div>
    </div>
    <div class="story-card">${s.narrative}</div>
    <div class="question-box">🤔 ${s.question}</div>
    <div class="choices" id="choices">
      ${s.choices.map((c,i)=>`<button class="choice-btn" onclick="choose(${idx},${i})">${c.text}</button>`).join('')}
    </div>
    <div class="feedback" id="feedback"></div>
    <button class="next-btn" id="next-btn" style="display:none" onclick="goNext(${idx})">
      ${idx<STORIES.length-1?'Continue the Journey →':'See My Journey ✨'}
    </button>`;
  document.getElementById('screen-home').classList.remove('active');
  document.getElementById('screen-final').classList.remove('active');
  el.classList.add('active');
}

function choose(idx,ci){
  if(answered)return;
  answered=true;
  const s=STORIES[idx];
  const btns=document.querySelectorAll('#choices .choice-btn');
  btns.forEach(b=>b.disabled=true);
  const correct=s.choices[ci].correct;
  if(correct){score++;btns[ci].classList.add('correct');}
  else{btns[ci].classList.add('wrong');s.choices.forEach((c,i)=>{if(c.correct)btns[i].classList.add('correct');});}
  truths.push(s.truth);
  const fb=document.getElementById('feedback');
  fb.innerHTML=`<span class="feedback-emoji">${correct?'🌟 You got it!':'💛 Keep searching!'}</span>${correct?s.goodFeedback:s.tryFeedback}<div class="truth-badge"><span class="badge-label">✦ Today's Truth ✦</span>${s.truth}</div>`;
  fb.className=`feedback ${correct?'good':'try-again'} show`;
  document.getElementById('next-btn').style.display='block';
}

function goNext(idx){
  if(idx<STORIES.length-1)showStory(idx+1);else showFinal();
}

function showFinal(){
  const el=document.getElementById('screen-final');
  const msg=score===5?"You walked every step with Yeshua today! 🌟":score>=3?"You are learning to walk in God's ways! 🌿":"Every journey starts with one step — keep seeking! ✨";
  el.innerHTML=`
    <div class="final-heading"><h1>Journey Complete!</h1><p>Luke 2 — Walking with Yeshua</p></div>
    <div class="score-circle"><div class="score-num">${score}</div><div class="score-denom">of ${STORIES.length} stars</div></div>
    <div class="score-message">${msg}</div>
    <div class="truths-card">
      <div class="truths-heading">✦ Truths You Collected ✦</div>
      ${truths.map(t=>`<div class="truth-line">${t}</div>`).join('')}
    </div>
    <div class="verse-card">
      <div class="ref">Luke 2:52</div>
      <div class="verse-text">"And Yeshua grew in wisdom and stature, and in favor with God and with people."</div>
      <div class="verse-note">That is our goal too — to keep growing every day. 🌱</div>
    </div>
    <button class="replay-btn" onclick="resetGame()">Play Again 🌟</button>`;
  document.getElementById('screen-story').classList.remove('active');
  el.classList.add('active');
}

function resetGame(){
  current=0;score=0;truths=[];
  document.getElementById('screen-final').classList.remove('active');
  document.getElementById('screen-home').classList.add('active');
}
</script>
</body>
</html>
