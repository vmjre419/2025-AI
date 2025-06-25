<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>⌨️타자 연습</title>
<style>
body {
  background: linear-gradient(135deg, #f9d4ca 0%, #f6e7fa 100%);
  font-family: 'Segoe UI', 'Malgun Gothic', Arial, sans-serif;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  margin: 0;
}
.main-wrap {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  margin-top: 48px;
}
.folder-tabs {
  display: flex;
  gap: 16px;
  margin-left: 24px;
  margin-top: 0;
  position: relative;
  z-index: 3;
}
.tab-btn {
  background: #fff;
  border: 2px solid #a1c4fd;
  border-bottom: none;
  border-radius: 18px 18px 0 0;
  padding: 12px 36px;
  font-size: 1.2rem;
  font-weight: 700;
  color: #a1c4fd;
  cursor: pointer;
  box-shadow: 0 2px 8px rgba(161,196,253,0.10);
  transition: background 0.2s, color 0.2s;
  outline: none;
  position: relative;
  top: 8px;
}
.tab-btn.active {
  background: linear-gradient(90deg, #fcb69f 0%, #a1c4fd 100%);
  color: #fff;
  border-bottom: 2px solid #fff;
  z-index: 2;
}
.container {
  background: rgba(255,255,255,0.95);
  border-radius: 32px;
  box-shadow: 0 8px 32px rgba(0,0,0,0.10);
  padding: 64px 48px 56px 48px;
  max-width: 900px;
  width: 90vw;
  min-height: 420px;
  text-align: center;
  margin-top: 0;
}
.stats {
  display: flex;
  justify-content: space-around;
  margin-bottom: 16px;
  font-size: 1.25rem;
  color: #333;
  font-weight: 700;
  gap: 32px;
}
.stats .avg {
  color: #ff9800;
  font-weight: 900;
  font-size: 1.1em;
  margin-left: 8px;
}
.sentence {
  font-size: 1.6rem;
  margin-bottom: 32px;
  letter-spacing: 1.5px;
  word-break: break-word;
  background: linear-gradient(90deg, #fcb69f 0%, #a1c4fd 100%);
  color: #fff;
  border-radius: 18px;
  padding: 24px 18px;
  box-shadow: 0 2px 12px rgba(252,182,159,0.12);
  font-weight: 600;
  transition: background 0.3s;
}
.sentence span.correct {
  color: #fff;
  background: #FFD600;
  border-radius: 6px;
  padding: 2px 3px;
}
.sentence span.incorrect {
  color: #fff;
  background: #f87171;
  border-radius: 6px;
  padding: 2px 3px;
  text-decoration: underline;
}
.input-area {
  width: 100%;
  max-width: 100%;
  box-sizing: border-box;
  padding: 18px;
  font-size: 1.3rem;
  border: none;
  border-radius: 18px;
  outline: none;
  margin-bottom: 24px;
  background: #f6e7fa;
  box-shadow: 0 2px 8px rgba(161,196,253,0.10);
  color: #333;
  text-align: center;
  transition: box-shadow 0.2s;
}
.input-area:focus {
  box-shadow: 0 4px 16px rgba(252,182,159,0.18);
  background: #fff;
}
.result {
  margin-top: 18px;
  font-size: 1.2rem;
  color: #f87171;
  font-weight: 600;
  background: #fff0f0;
  border-radius: 12px;
  padding: 10px 0;
  box-shadow: 0 1px 4px rgba(248,113,113,0.08);
  display: block;
}
.start-btn {
  background: linear-gradient(90deg, #fcb69f 0%, #a1c4fd 100%);
  color: #fff;
  border: none;
  border-radius: 18px;
  padding: 12px 36px;
  font-size: 1.2rem;
  cursor: pointer;
  margin-top: 12px;
  font-weight: 600;
  box-shadow: 0 2px 8px rgba(161,196,253,0.10);
  transition: background 0.2s;
}
.start-btn:hover {
  background: linear-gradient(90deg, #a1c4fd 0%, #fcb69f 100%);
}
.results-row {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: flex-start;
  gap: 32px;
  margin-top: 24px;
}
.results-col {
  flex: 1 1 320px;
  min-width: 280px;
  max-width: 480px;
}
.ranking {
  background: rgba(255,255,255,0.92);
  border-radius: 18px;
  box-shadow: 0 2px 12px rgba(161,196,253,0.10);
  padding: 18px 0 10px 0;
  width: 100%;
  margin: 0 auto;
}
.ranking-title {
  font-size: 1.2rem;
  font-weight: 700;
  color: #a1c4fd;
  margin-bottom: 10px;
}
.rank-list {
  list-style: none;
  padding: 0;
  margin: 0;
}
.rank-item {
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.1rem;
  font-weight: 600;
  color: #333;
  margin-bottom: 6px;
  gap: 10px;
}
.name-input {
  border: 1.5px solid #a1c4fd;
  border-radius: 8px;
  padding: 6px 12px;
  font-size: 1.1rem;
  margin-left: 8px;
  outline: none;
}
.name-btn {
  background: linear-gradient(90deg, #fcb69f 0%, #a1c4fd 100%);
  color: #fff;
  border: none;
  border-radius: 8px;
  padding: 6px 16px;
  font-size: 1.1rem;
  margin-left: 6px;
  cursor: pointer;
  font-weight: 600;
}
.name-btn:hover {
  background: linear-gradient(90deg, #a1c4fd 0%, #fcb69f 100%);
}
.input-bar {
  display: flex;
  justify-content: flex-start;
  align-items: center;
  gap: 8px;
  margin: 12px 0;
}
#manageContainer {
  display: flex;
  flex-direction: row;
  gap: 48px;
}
.manage-col {
  flex: 1;
  text-align: left;
}
.manage-col ul {
  padding-left: 20px;
}
.manage-col li {
  margin-bottom: 8px;
}
.delete-btn {
  background: none;
  border: none;
  color: #f87171;
  font-size: 1.1rem;
  font-weight: bold;
  margin-left: 8px;
  cursor: pointer;
}
.manage-scroll {
  max-height: 300px;
  overflow-y: auto;
  padding-right: 8px;
}
.name-btn {
  padding: 4px 8px;
  font-size: 0.9rem;
  line-height: 1;
}
.delete-btn {
  font-size: 0.9rem;
  padding: 2px 6px;
  line-height: 1;
}
</style>
</head>
<body>
  <div class="main-wrap">
    <div class="folder-tabs">
      <button id="tabWord" class="tab-btn active">단어</button>
      <button id="tabSentence" class="tab-btn">단문</button>
      <button id="tabManage" class="tab-btn">관리</button>
    </div>

    <div class="container" id="wordContainer">
      <div class="stats">
        <div>타자속도: <span id="wordSpeed">0</span>타 <span class="avg" id="wordAvgSpeed"></span></div>
        <div>정확도: <span id="wordAccuracy">100</span>%</div>
      </div>
      <div class="sentence" id="wordSentence"></div>
      <input type="text" id="wordInput" class="input-area" placeholder="여기에 타자로 입력하세요." autocomplete="off" />
      <div class="results-row">
        <div class="results-col"><div id="wordResults"></div></div>
        <div class="results-col">
          <div class="ranking">
            <div class="ranking-title">🏆 단어 타자속도 TOP 5</div>
            <ul class="rank-list" id="wordRankList"></ul>
          </div>
        </div>
      </div>
    </div>

    <div class="container" id="sentenceContainer" style="display:none;">
      <div class="stats">
        <div>타자속도: <span id="speed">0</span>타 <span class="avg" id="sentenceAvgSpeed"></span></div>
        <div>정확도: <span id="accuracy">100</span>%</div>
      </div>
      <div class="sentence" id="sentence"></div>
      <input type="text" id="input" class="input-area" placeholder="여기에 타자로 입력하세요." autocomplete="off" />
      <div class="results-row">
        <div class="results-col"><div id="results"></div></div>
        <div class="results-col">
          <div class="ranking">
            <div class="ranking-title">🏆 단문 타자속도 TOP 5</div>
            <ul class="rank-list" id="rankList"></ul>
          </div>
        </div>
      </div>
    </div>

    <div class="container" id="manageContainer" style="display:none;">
      <div style="display: flex; gap: 32px;">
        <div style="flex:1">
          <h3>🛠️ 단어 관리</h3>
          <div class="input-bar">
            <input id="manageWordInput" class="name-input" placeholder="새 단어 입력"/>
            <button id="addWordBtn" class="name-btn">추가</button>
          </div>
          <ul id="wordListUl" class="manage-scroll"></ul>
        </div>
        <div style="flex:1">
          <h3>🛠️ 단문 관리</h3>
          <div class="input-bar">
            <input id="manageSentenceInput" class="name-input" placeholder="새 문장 입력"/>
            <button id="addSentenceBtn" class="name-btn">추가</button>
          </div>
<ul id="sentenceListUl" class="manage-scroll"></ul>        </div>
      </div>
    </div>
  </div>

  <script>
  document.addEventListener('DOMContentLoaded', function() {
    const tabWord = document.getElementById('tabWord');
    const tabSentence = document.getElementById('tabSentence');
    const tabManage = document.getElementById('tabManage');
    const wordContainer = document.getElementById('wordContainer');
    const sentenceContainer = document.getElementById('sentenceContainer');
    const manageContainer = document.getElementById('manageContainer');

    const wordSentenceDiv = document.getElementById('wordSentence');
    const wordInput = document.getElementById('wordInput');
    const wordSpeedSpan = document.getElementById('wordSpeed');
    const wordAccuracySpan = document.getElementById('wordAccuracy');
    const wordAvgSpeed = document.getElementById('wordAvgSpeed');
    const wordResultsDiv = document.getElementById('wordResults');
    const wordRankList = document.getElementById('wordRankList');

    const sentence = document.getElementById('sentence');
    const input = document.getElementById('input');
    const speedSpan = document.getElementById('speed');
    const accuracySpan = document.getElementById('accuracy');
    const sentenceAvgSpeed = document.getElementById('sentenceAvgSpeed');
    const resultsDiv = document.getElementById('results');
    const rankList = document.getElementById('rankList');

    function showTab(tab) {
      tabWord.classList.remove('active');
      tabSentence.classList.remove('active');
      tabManage.classList.remove('active');
      wordContainer.style.display = 'none';
      sentenceContainer.style.display = 'none';
      manageContainer.style.display = 'none';
      if (tab === 'word') {
        tabWord.classList.add('active');
        wordContainer.style.display = '';
      } else if (tab === 'sentence') {
        tabSentence.classList.add('active');
        sentenceContainer.style.display = '';
      } else {
        tabManage.classList.add('active');
        manageContainer.style.display = '';
      }
    }
    tabWord.onclick = () => showTab('word');
    tabSentence.onclick = () => showTab('sentence');
    tabManage.onclick = () => { showTab('manage'); renderManageList(); };

    function saveWordList(list) { localStorage.setItem('typingWordList', JSON.stringify(list)); }
    function loadWordList() {
      try { const arr = JSON.parse(localStorage.getItem('typingWordList')); if (Array.isArray(arr) && arr.length) return arr; }
      catch(e){}
      return ['사과','바나나','컴퓨터','학교','행복'];
    }
    function saveSentenceList(list) { localStorage.setItem('typingSentenceList', JSON.stringify(list)); }
    function loadSentenceList() {
      try { const arr = JSON.parse(localStorage.getItem('typingSentenceList')); if (Array.isArray(arr) && arr.length) return arr; }
      catch(e){}
      return [
        '인공지능은 미래의 핵심 기술입니다.',
        '타자 연습을 꾸준히 하면 속도가 빨라집니다.',
        '프로그래밍은 논리적 사고를 키워줍니다.',
        '오늘도 즐거운 하루 보내세요!',
        'AI와 메타버스는 다양한 분야에 활용됩니다.'
      ];
    }
    let wordList = loadWordList();
    let sentences = loadSentenceList();

    window.renderManageList = function() {
      const ulW = document.getElementById('wordListUl');
      ulW.innerHTML = '';
      wordList.forEach((w,i) => {
        const li = document.createElement('li');
        li.innerHTML = `${w} <button class="name-btn" onclick="removeWord(${i})">✕</button>`;
        ulW.appendChild(li);
      });
      const ulS = document.getElementById('sentenceListUl');
      ulS.innerHTML = '';
      sentences.forEach((s,i) => {
        const li = document.createElement('li');
        li.innerHTML = `${s} <button class="name-btn" onclick="removeSentence(${i})">✕</button>`;
        ulS.appendChild(li);
      });
    };
    window.removeWord = function(i){ wordList.splice(i,1); saveWordList(wordList); renderManageList(); };
    window.removeSentence = function(i){ sentences.splice(i,1); saveSentenceList(sentences); renderManageList(); };
    document.getElementById('addWordBtn').onclick = () => {
      const v = document.getElementById('manageWordInput').value.trim();
      if (v && !wordList.includes(v)) { wordList.push(v); saveWordList(wordList); renderManageList(); }
      document.getElementById('manageWordInput').value='';
    };
    document.getElementById('addSentenceBtn').onclick = () => {
      const v = document.getElementById('manageSentenceInput').value.trim();
      if (v && !sentences.includes(v)) { sentences.push(v); saveSentenceList(sentences); renderManageList(); }
      document.getElementById('manageSentenceInput').value='';
    };

    // --- 단어 기능 전체 (생략 없이 붙여넣음) ---
    let wordSpeeds=[], currentWord='', wordStartTime=0, wordEndTime=0,
        wordCorrectCount=0, wordTotalTyped=0, wordFinished=false,
        wordRecords=[], wordRecordsDate='';
    function pickWord(){ currentWord = wordList[Math.floor(Math.random()*wordList.length)]; }
    function renderWord(){
      const val = wordInput.value;
      let html='';
      for(let i=0;i<currentWord.length;i++){
        if(val[i]==null) html+=`<span>${currentWord[i]}</span>`;
        else if(val[i]===currentWord[i]) html+=`<span class='correct'>${currentWord[i]}</span>`;
        else html+=`<span class='incorrect'>${currentWord[i]}</span>`;
      }
      wordSentenceDiv.innerHTML = html;
    }
    function updateWordStatsRealtime(){
      if(!wordStartTime||wordFinished){ wordSpeedSpan.textContent='0'; wordAccuracySpan.textContent='100'; wordAvgSpeed.textContent=''; return; }
      const now=Date.now(), t=(now-wordStartTime)/1000;
      const wpm = wordTotalTyped>0 && t>0 ? Math.round((wordTotalTyped/5)/(t/60)) : 0;
      const acc = wordTotalTyped>0 ? Math.round((wordCorrectCount/wordTotalTyped)*100) : 100;
      wordSpeedSpan.textContent=wpm;
      wordAccuracySpan.textContent=acc;
      if(wordSpeeds.length>0){
        const avg=Math.round(wordSpeeds.reduce((a,b)=>a+b,0)/wordSpeeds.length);
        wordAvgSpeed.textContent=`(평균 ${avg}타)`;
      }
    }
    function resetWordStats(){ wordSpeedSpan.textContent='0'; wordAccuracySpan.textContent='100'; wordAvgSpeed.textContent=''; }
    function getWordTodayStr(){
      const d=new Date();
      return `${d.getFullYear()}-${String(d.getMonth()+1).padStart(2,'0')}-${String(d.getDate()).padStart(2,'0')}`;
    }
    function checkResetWordRecords(){
      const t=getWordTodayStr();
      if(wordRecordsDate!==t){ wordRecords=[]; wordRecordsDate=t; saveWordRecords(); updateWordRanking(); }
    }
    function saveWordRecords(){ localStorage.setItem('typingWordRecords', JSON.stringify({wordRecords,wordRecordsDate})); }
    function loadWordRecords(){
      try{
        const obj=JSON.parse(localStorage.getItem('typingWordRecords'));
        if(obj && Array.isArray(obj.wordRecords) && typeof obj.wordRecordsDate==='string'){
          wordRecords=obj.wordRecords;
          wordRecordsDate=obj.wordRecordsDate;
        }
      }catch(e){}
    }
    function updateWordRanking(){
      checkResetWordRecords();
      const sorted=[...wordRecords].sort((a,b)=>b.wpm-a.wpm).slice(0,5);
      wordRankList.innerHTML='';
      sorted.forEach((rec,i)=>{
        const icon = i===0?'👑':i===1?'🥈':i===2?'🥉':'';
        const nameHtml = rec.name
          ? `<span style="margin-left:8px;font-weight:700;color:${i<=2?'#1976d2':'#222'}">${rec.name}</span>`
          : `<input id="wordNameInput${i+1}" class="name-input" maxlength="8" placeholder="이름"/><button id="wordNameBtn${i+1}" class="name-btn">저장</button>`;
        const li=document.createElement('li');
        li.className='rank-item';
        li.innerHTML = `${icon}<span>${i+1}위</span> <span style="color:#1976d2;font-weight:900;">${rec.wpm}타</span> <span style="color:#f87171;">(${rec.accuracy}% 정확도)</span> ${nameHtml}`;
        wordRankList.appendChild(li);
      });
      [1,2,3].forEach(i=>{
        const btn=document.getElementById(`wordNameBtn${i}`);
        if(btn){
          btn.onclick=function(){
            let v = document.getElementById(`wordNameInput${i}`).value.trim();
            if(!v){ alert('이름을 입력하세요!'); return; }
            if(v.length>8) v=v.slice(0,8);
            const sorted=[...wordRecords].sort((a,b)=>b.wpm-a.wpm).slice(0,5);
            if(sorted[i-1]){
              sorted[i-1].name=v;
              const idx=wordRecords.indexOf(sorted[i-1]);
              if(idx!==-1) wordRecords[idx].name=v;
              saveWordRecords();
              updateWordRanking();
            }
          };
        }
      });
    }
    wordInput.addEventListener('input',()=>{
      if(wordFinished)return;
      if(wordInput.value.length===1&&!wordStartTime) wordStartTime=Date.now();
      wordTotalTyped=wordInput.value.length;
      wordCorrectCount=0;
      for(let i=0;i<wordTotalTyped;i++) if(wordInput.value[i]===currentWord[i]) wordCorrectCount++;
      renderWord();
      updateWordStatsRealtime();
      if(wordInput.value===currentWord) finishWord();
    });
    wordInput.addEventListener('keydown', e => {
    if (e.key === 'Enter' && wordFinished) {
        wordInput.disabled = false;
        wordInput.value = '';
        wordStartTime = 0;
        wordFinished = false;
        pickWord();
        renderWord();
        resetWordStats();
        wordInput.focus();
    }
    });
    input.addEventListener('keydown', e => {
    if (e.key === 'Enter' && finished) {
        input.disabled = false;
        input.value = '';
        startTime = 0;
        finished = false;
        pickSentence();
        renderSentence();
        updateStatsRealtime();
        input.focus();
    }
    });

    function finishWord(){
      if(wordFinished)return;
      wordFinished=true;
      wordEndTime=Date.now();
      const t=(wordEndTime-wordStartTime)/1000;
      const wpm=wordTotalTyped>0&&t>0?Math.round((wordTotalTyped/5)/(t/60)):0;
      const acc=wordTotalTyped>0?Math.round((wordCorrectCount/wordTotalTyped)*100):100;
      wordSpeedSpan.textContent=wpm;
      wordAccuracySpan.textContent=acc;
      wordSpeeds.push(wpm);
      resetWordStats();
      wordResultsDiv.innerHTML = `<div class="result">🎉 <b>완료!</b><br>타자속도: <b>${wpm}</b>타<br>정확도: <b>${acc}</b>%</div>`;
      checkResetWordRecords();
      wordRecords.push({wpm,accuracy:acc,date:getWordTodayStr()});
      saveWordRecords(); updateWordRanking();
      wordInput.disabled=true;
      setTimeout(()=>{
        wordInput.disabled=false;
        wordInput.value=''; wordStartTime=0; wordFinished=false;
        pickWord(); renderWord(); resetWordStats();
      },800);
    }

    // --- 문장 기능 전체 (생략 없이 붙여넣음) ---
    let sentenceSpeeds=[],currentSentence='',startTime=0,endTime=0,correctCount=0,totalTypedSentence=0,finished=false,records=[],recordsDate='';
    function pickSentence(){ currentSentence = sentences[Math.floor(Math.random()*sentences.length)]; }
    function renderSentence(){
      const val=input.value; let html='';
      for(let i=0;i<currentSentence.length;i++){
        if(val[i]==null) html+=`<span>${currentSentence[i]}</span>`;
        else if(val[i]===currentSentence[i]) html+=`<span class='correct'>${currentSentence[i]}</span>`;
        else html+=`<span class='incorrect'>${currentSentence[i]}</span>`;
      }
      sentence.innerHTML=html;
    }
    function updateStatsRealtime(){
      if(!startTime||finished){ speedSpan.textContent='0'; accuracySpan.textContent='100'; sentenceAvgSpeed.textContent=''; return; }
      const now=Date.now(),t=(now-startTime)/1000;
      const wpm=totalTypedSentence>0&&t>0?Math.round((totalTypedSentence/5)/(t/60)):0;
      const acc=totalTypedSentence>0?Math.round((correctCount/totalTypedSentence)*100):100;
      speedSpan.textContent=wpm; accuracySpan.textContent=acc;
      if(sentenceSpeeds.length>0){
        const avg=Math.round(sentenceSpeeds.reduce((a,b)=>a+b,0)/sentenceSpeeds.length);
        sentenceAvgSpeed.textContent=`(평균 ${avg}타)`;
      }
    }
    function getTodayStr(){
      const d=new Date();
      return `${d.getFullYear()}-${String(d.getMonth()+1).padStart(2,'0')}-${String(d.getDate()).padStart(2,'0')}`;
    }
    function checkResetRecords(){
      const t=getTodayStr();
      if(recordsDate!==t){ records=[]; recordsDate=t; saveRecords(); updateRanking(); }
    }
    function saveRecords(){ localStorage.setItem('typingRecords',JSON.stringify({records,recordsDate})); }
    function loadRecords(){
      try{
        const obj=JSON.parse(localStorage.getItem('typingRecords'));
        if(obj && Array.isArray(obj.records)&&typeof obj.recordsDate==='string'){
          records=obj.records;recordsDate=obj.recordsDate;
        }
      }catch(e){}
    }
    function updateRanking(){
      checkResetRecords();
      const sorted=[...records].sort((a,b)=>b.wpm-a.wpm).slice(0,5);
      rankList.innerHTML='';
      sorted.forEach((rec,i)=>{
        const icon = i===0?'👑':i===1?'🥈':i===2?'🥉':'';
        const nameHtml = rec.name
          ? `<span style="margin-left:8px;font-weight:700;color:${i<=2?'#1976d2':'#222'}">${rec.name}</span>`
          : `<input id="nameInput${i+1}" class="name-input" maxlength="8" placeholder="이름"/><button id="nameBtn${i+1}" class="name-btn">저장</button>`;
        const li=document.createElement('li');
        li.className='rank-item';
        li.innerHTML = `${icon}<span>${i+1}위</span> <span style="color:#1976d2;font-weight:900;">${rec.wpm}타</span> <span style="color:#f87171;">(${rec.accuracy}% 정확도)</span> ${nameHtml}`;
        rankList.appendChild(li);
      });
      [1,2,3].forEach(i=>{
        const btn=document.getElementById(`nameBtn${i}`);
        if(btn){
          btn.onclick=function(){
            let v=document.getElementById(`nameInput${i}`).value.trim();
            if(!v){ alert('이름을 입력하세요!'); return; }
            if(v.length>8)v=v.slice(0,8);
            const sorted=[...records].sort((a,b)=>b.wpm-a.wpm).slice(0,5);
            if(sorted[i-1]){
              sorted[i-1].name=v;
              const idx=records.indexOf(sorted[i-1]);
              if(idx!==-1)records[idx].name=v;
              saveRecords(); updateRanking();
            }
          };
        }
      });
    }
    input.addEventListener('input',()=>{
      if(finished) return;
      if(input.value.length===1&&!startTime) startTime=Date.now();
      totalTypedSentence=input.value.length;correctCount=0;
      for(let i=0;i<totalTypedSentence;i++) if(input.value[i]===currentSentence[i]) correctCount++;
      renderSentence(); updateStatsRealtime();
      if(input.value===currentSentence) finishSentence();
    });
    function finishSentence(){
      if(finished)return;
      finished=true;endTime=Date.now();
      const t=(endTime-startTime)/1000;
      const wpm=totalTypedSentence>0&&t>0?Math.round((totalTypedSentence/5)/(t/60)):0;
      const acc=totalTypedSentence>0?Math.round((correctCount/totalTypedSentence)*100):100;
      speedSpan.textContent=wpm; accuracySpan.textContent=acc;
      sentenceSpeeds.push(wpm);
      resultsDiv.innerHTML=`<div class="result">🎉 <b>완료!</b><br>타자속도: <b>${wpm}</b>타<br>정확도: <b>${acc}</b>%</div>`;
      checkResetRecords();
      records.push({wpm,accuracy:acc,date:getTodayStr()});
      saveRecords(); updateRanking();
      input.disabled=true;
      setTimeout(()=>{
        input.disabled=false; input.value=''; startTime=0; finished=false;
        pickSentence(); renderSentence(); updateStatsRealtime();
      },800);
    }

    // 탭 자동 초기 및 기록 로드
    loadWordRecords(); loadRecords();
    pickWord(); renderWord(); updateWordRanking();
    pickSentence(); renderSentence(); updateRanking();
    showTab('word');
  });
  </script>
</body>
</html>
