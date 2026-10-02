# -
나는 어떤 너진똑일까? 너진똑 성격 테스트!

```html
<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>나의 MBTI 정원 🌷</title>

<style>
@import url('https://fonts.googleapis.com/css2?family=Jua&family=Noto+Sans+KR:wght@400;500;700&display=swap');

* {
    box-sizing: border-box;
}

body {
    margin: 0;
    min-height: 100vh;
    font-family: 'Noto Sans KR', sans-serif;
    background: linear-gradient(135deg, #fff4fb, #f1f7ff);
    color: #454052;
}

button {
    font-family: inherit;
}

.container {
    width: min(720px, calc(100% - 32px));
    margin: 0 auto;
}

/* 시작 화면 */

#startScreen {
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;
}

.start-card {
    background: rgba(255,255,255,.88);
    border-radius: 32px;
    padding: 55px 35px;
    box-shadow: 0 15px 50px rgba(130,110,150,.12);
}

.flower {
    font-size: 60px;
    margin-bottom: 10px;
}

h1 {
    font-family: 'Jua', sans-serif;
    font-size: 42px;
    margin: 10px 0;
}

.subtitle {
    color: #88818f;
    line-height: 1.7;
    margin-bottom: 35px;
}

.start-btn,
.retry-btn {
    border: 0;
    padding: 16px 42px;
    border-radius: 50px;
    background: #ff91bd;
    color: white;
    font-size: 18px;
    font-weight: 700;
    cursor: pointer;
    box-shadow: 0 7px 18px rgba(255,145,189,.3);
    transition: .2s;
}

.start-btn:hover,
.retry-btn:hover {
    transform: translateY(-3px);
}

/* 테스트 */

#testScreen,
#resultScreen {
    display: none;
    padding: 45px 0;
}

.progress-info {
    display: flex;
    justify-content: space-between;
    font-size: 14px;
    color: #918a98;
    margin-bottom: 10px;
}

.progress-bar {
    height: 9px;
    background: #eee8f0;
    border-radius: 20px;
    overflow: hidden;
    margin-bottom: 35px;
}

.progress {
    height: 100%;
    width: 0;
    background: linear-gradient(90deg, #ff91bd, #a995ff);
    transition: .3s;
}

.question-card {
    background: white;
    border-radius: 30px;
    padding: 45px 35px;
    box-shadow: 0 15px 45px rgba(100,90,120,.1);
}

.question-number {
    color: #ff75ad;
    font-weight: 700;
    margin-bottom: 15px;
}

.question {
    font-family: 'Jua', sans-serif;
    font-size: 28px;
    line-height: 1.45;
    margin-bottom: 35px;
}

.answers {
    display: flex;
    flex-direction: column;
    gap: 15px;
}

.answer {
    border: 2px solid #eeeaf0;
    background: #fff;
    border-radius: 20px;
    padding: 20px;
    text-align: left;
    cursor: pointer;
    font-size: 16px;
    transition: .2s;
}

.answer:hover {
    border-color: #ff9fc3;
    background: #fff7fa;
    transform: translateY(-2px);
}

/* 결과 */

.result-card {
    background: white;
    border-radius: 35px;
    overflow: hidden;
    box-shadow: 0 18px 60px rgba(100,90,120,.13);
}

.result-top {
    text-align: center;
    padding: 45px 30px 35px;
}

.result-emoji {
    font-size: 80px;
}

.result-type {
    font-family: 'Jua', sans-serif;
    font-size: 60px;
    margin: 5px 0;
}

.result-name {
    font-size: 21px;
    font-weight: 700;
    margin-bottom: 15px;
}

.result-description {
    color: #77717f;
    line-height: 1.8;
    max-width: 550px;
    margin: auto;
}

.result-body {
    padding: 30px;
}

.info-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 14px;
}

.info {
    background: #faf8fb;
    border-radius: 20px;
    padding: 18px;
}

.info-title {
    font-size: 13px;
    color: #9a929f;
    margin-bottom: 5px;
}

.info-value {
    font-weight: 700;
}

.traits {
    margin-top: 25px;
}

.traits h3 {
    font-family: 'Jua', sans-serif;
    font-size: 23px;
}

.tag {
    display: inline-block;
    padding: 8px 13px;
    border-radius: 30px;
    background: #fff0f6;
    color: #e66d9d;
    margin: 4px;
    font-size: 13px;
}

.retry-wrap {
    text-align: center;
    margin-top: 30px;
}

@media (max-width: 600px) {

    h1 {
        font-size: 34px;
    }

    .question-card {
        padding: 30px 22px;
    }

    .question {
        font-size: 24px;
    }

    .result-type {
        font-size: 48px;
    }

    .info-grid {
        grid-template-columns: 1fr;
    }
}
</style>
</head>

<body>

<!-- 시작 화면 -->

<section id="startScreen">
    <div class="container">
        <div class="start-card">
            <div class="flower">🌷</div>

            <h1>나의 MBTI 정원</h1>

            <p class="subtitle">
                32개의 질문으로 알아보는<br>
                나만의 작은 성격 정원 🌿
            </p>

            <button class="start-btn" onclick="startTest()">
                테스트 시작하기
            </button>
        </div>
    </div>
</section>


<!-- 테스트 화면 -->

<section id="testScreen">
    <div class="container">

        <div class="progress-info">
            <span id="questionCount">1 / 32</span>
            <span id="dimension">E · I</span>
        </div>

        <div class="progress-bar">
            <div class="progress" id="progress"></div>
        </div>

        <div class="question-card">

            <div class="question-number" id="questionNumber">
                QUESTION 01
            </div>

            <div class="question" id="question">
                질문
            </div>

            <div class="answers">
                <button class="answer" id="answerA" onclick="selectAnswer(0)">
                    A
                </button>

                <button class="answer" id="answerB" onclick="selectAnswer(1)">
                    B
                </button>
            </div>

        </div>
    </div>
</section>


<!-- 결과 화면 -->

<section id="resultScreen">
    <div class="container">

        <div class="result-card">

            <div class="result-top" id="resultTop">

                <div class="result-emoji" id="resultEmoji"></div>

                <div class="result-type" id="resultType"></div>

                <div class="result-name" id="resultName"></div>

                <p class="result-description" id="resultDescription"></p>

            </div>

            <div class="result-body">

                <div class="info-grid">

                    <div class="info">
                        <div class="info-title">🌈 어울리는 색</div>
                        <div class="info-value" id="resultColor"></div>
                    </div>

                    <div class="info">
                        <div class="info-title">🍰 어울리는 것</div>
                        <div class="info-value" id="resultFood"></div>
                    </div>

                    <div class="info">
                        <div class="info-title">🐰 닮은 동물</div>
                        <div class="info-value" id="resultAnimal"></div>
                    </div>

                    <div class="info">
                        <div class="info-title">🌿 분위기</div>
                        <div class="info-value" id="resultMood"></div>
                    </div>

                </div>

                <div class="traits">
                    <h3>당신의 키워드</h3>
                    <div id="resultTraits"></div>
                </div>

                <div class="retry-wrap">
                    <button class="retry-btn" onclick="restartTest()">
                        다시 테스트하기 🌷
                    </button>
                </div>

            </div>
        </div>
    </div>
</section>


<script>

/* =========================
   32개 질문
========================= */

const questions = [

/* E / I */

{
    q:"주말에 아무런 약속이 없다면?",
    a:"친구에게 연락해서 같이 놀 일을 만든다.",
    b:"혼자 편하게 쉬면서 시간을 보낸다.",
    x:"E"
},
{
    q:"새로운 모임에 들어갔을 때 나는?",
    a:"먼저 말을 걸어보는 편이다.",
    b:"분위기를 살피면서 천천히 적응한다.",
    x:"E"
},
{
    q:"기분이 안 좋을 때 나는?",
    a:"누군가와 이야기하면서 풀리는 편이다.",
    b:"혼자 생각할 시간이 필요하다.",
    x:"I"
},
{
    q:"재미있는 일이 생겼을 때?",
    a:"바로 누군가에게 이야기하고 싶다.",
    b:"혼자 먼저 즐기고 나중에 이야기한다.",
    x:"E"
},
{
    q:"친구들과 하루 종일 놀고 집에 돌아오면?",
    a:"아직 더 놀고 싶다.",
    b:"혼자만의 시간이 필요하다.",
    x:"I"
},
{
    q:"발표나 모임에서?",
    a:"사람들 앞에서 말하는 것이 비교적 편하다.",
    b:"가능하면 조용히 있는 편이다.",
    x:"E"
},
{
    q:"처음 만난 사람과 대화할 때?",
    a:"생각보다 쉽게 대화를 시작한다.",
    b:"무슨 말을 해야 할지 잠시 생각한다.",
    x:"I"
},
{
    q:"혼자 있는 시간이 길어지면?",
    a:"사람들이 조금 그리워진다.",
    b:"오히려 편안하고 좋다.",
    x:"I"
},

/* S / N */

{
    q:"친구가 여행 이야기를 한다면?",
    a:"어디에 갔고 무엇을 했는지가 궁금하다.",
    b:"그 여행에서 어떤 느낌을 받았는지가 궁금하다.",
    x:"S"
},
{
    q:"설명서를 볼 때 나는?",
    a:"적힌 순서대로 따라가는 편이다.",
    b:"대충 이해하고 내 방식대로 해보는 편이다.",
    x:"S"
},
{
    q:"새로운 아이디어가 떠오르면?",
    a:"실제로 가능한지부터 생각한다.",
    b:"일단 상상부터 크게 펼쳐본다.",
    x:"N"
},
{
    q:"영화를 보고 난 뒤 더 기억에 남는 것은?",
    a:"구체적인 장면과 사건이다.",
    b:"영화가 전달하려던 의미와 분위기다.",
    x:"N"
},
{
    q:"무언가를 배울 때?",
    a:"예시를 많이 보는 것이 이해하기 쉽다.",
    b:"원리와 전체적인 개념부터 알고 싶다.",
    x:"S"
},
{
    q:"친구가 '나 요즘 힘들어'라고 한다면?",
    a:"무슨 일이 있었는지 구체적으로 묻는다.",
    b:"그 사람이 어떤 감정을 느끼는지 생각한다.",
    x:"N"
},
{
    q:"새로운 물건을 살 때?",
    a:"실용성과 실제 사용법을 중요하게 본다.",
    b:"디자인이나 가능성을 더 많이 본다.",
    x:"S"
},
{
    q:"미래를 생각할 때 나는?",
    a:"현실적으로 가능한 계획을 떠올린다.",
    b:"아직 일어나지 않은 다양한 가능성을 상상한다.",
    x:"N"
},

/* T / F */

{
    q:"친구가 고민을 털어놓았을 때?",
    a:"해결할 방법부터 같이 찾아준다.",
    b:"일단 공감하고 마음을 달래준다.",
    x:"T"
},
{
    q:"친구와 의견이 충돌하면?",
    a:"누가 더 논리적인지 생각한다.",
    b:"상대방이 상처받지 않았는지 생각한다.",
    x:"F"
},
{
    q:"무언가를 선택할 때?",
    a:"객관적으로 따져보고 결정한다.",
    b:"내 마음이 가는 쪽을 선택한다.",
    x:"T"
},
{
    q:"친구가 잘못한 일을 했다면?",
    a:"잘못한 점을 솔직하게 말해준다.",
    b:"상대방의 기분을 생각하며 조심스럽게 말한다.",
    x:"F"
},
{
    q:"논쟁을 할 때 나는?",
    a:"논리적으로 맞는 것이 중요하다.",
    b:"서로 기분 나쁘지 않게 끝내는 것이 중요하다.",
    x:"T"
},
{
    q:"누군가 나를 비판한다면?",
    a:"그 말이 논리적으로 맞는지 먼저 생각한다.",
    b:"그 사람이 왜 그렇게 말했는지 마음부터 생각한다.",
    x:"T"
},
{
    q:"선물을 고를 때?",
    a:"상대방에게 실제로 필요한 것을 고른다.",
    b:"상대방이 좋아할 만한 감성적인 것을 고른다.",
    x:"F"
},
{
    q:"친구가 약속을 어겼다면?",
    a:"왜 어겼는지 이유를 먼저 듣는다.",
    b:"서운한 감정을 먼저 이야기한다.",
    x:"F"
},

/* J / P */

{
    q:"여행을 간다면?",
    a:"미리 일정과 계획을 정해두는 편이다.",
    b:"그날그날 마음 가는 대로 움직이고 싶다.",
    x:"J"
},
{
    q:"시험 공부는?",
    a:"미리 계획을 세워두면 마음이 편하다.",
    b:"마감이 다가와야 집중이 잘 된다.",
    x:"P"
},
{
    q:"과제를 받으면?",
    a:"가능하면 빨리 끝내놓는다.",
    b:"시간이 있으니 나중에 해도 된다고 생각한다.",
    x:"J"
},
{
    q:"친구와 놀러 갈 때?",
    a:"어디에서 무엇을 할지 정해두는 게 좋다.",
    b:"일단 만나서 정하는 것도 재미있다.",
    x:"P"
},
{
    q:"방학 계획을 세운다면?",
    a:"하고 싶은 일을 미리 정리한다.",
    b:"그때그때 하고 싶은 일을 한다.",
    x:"P"
},
{
    q:"해야 할 일이 많을 때?",
    a:"순서대로 정리해서 하나씩 처리한다.",
    b:"그 순간 가장 하고 싶은 것부터 한다.",
    x:"J"
},
{
    q:"갑작스러운 약속 변경은?",
    a:"계획이 틀어져서 조금 불편하다.",
    b:"오히려 새로운 상황이 재미있다.",
    x:"P"
},
{
    q:"내 방이나 책상은?",
    a:"정리되어 있어야 마음이 편하다.",
    b:"조금 어질러져 있어도 크게 신경 쓰지 않는다.",
    x:"J"
}

];


/* =========================
   MBTI 결과
========================= */

const results = {

"ISTJ":{
emoji:"📚",
name:"차분한 계획가",
color:"크림 베이지",
food:"따뜻한 카라멜 푸딩",
animal:"부지런한 다람쥐",
mood:"정돈된 오후",
traits:["책임감","성실함","현실적","꼼꼼함"],
description:"맡은 일을 끝까지 해내려는 힘이 있는 사람이에요. 조용해 보여도 자신만의 기준이 분명하고, 해야 할 일을 차근차근 완성해가는 타입이에요."
},

"ISFJ":{
emoji:"🧸",
name:"포근한 수호자",
color:"밀크 핑크",
food:"딸기 우유",
animal:"토끼",
mood:"포근한 담요 속",
traits:["배려심","성실함","따뜻함","세심함"],
description:"주변 사람들의 작은 변화도 잘 알아차리는 따뜻한 사람이에요. 누군가에게는 아주 자연스럽게 의지가 되는 존재일지도 몰라요."
},

"INFJ":{
emoji:"🌙",
name:"조용한 꿈꾸는 사람",
color:"라벤더",
food:"블루베리 케이크",
animal:"사슴",
mood:"달빛이 비치는 숲",
traits:["통찰력","상상력","공감","신중함"],
description:"겉으로는 조용해 보여도 머릿속에서는 수많은 생각과 이야기가 펼쳐지고 있어요. 사람과 세상을 깊게 바라보는 편이에요."
},

"INTJ":{
emoji:"🔮",
name:"혼자 걷는 전략가",
color:"딥 퍼플",
food:"다크 초콜릿",
animal:"검은 고양이",
mood:"별이 가득한 밤",
traits:["독립적","분석적","전략적","집중력"],
description:"무언가를 이해할 때 겉으로 보이는 것보다 그 뒤에 있는 구조를 파악하려는 편이에요. 자신만의 방식으로 목표를 향해 가는 힘이 있어요."
},

"ISTP":{
emoji:"🛠️",
name:"쿨한 해결사",
color:"하늘색",
food:"레몬 소다",
animal:"고양이",
mood:"맑은 오후",
traits:["침착함","실용적","독립적","관찰력"],
description:"문제가 생기면 당황하기보다 직접 부딪혀 해결하려는 편이에요. 복잡한 설명보다 직접 해보면서 배우는 것을 좋아해요."
},

"ISFP":{
emoji:"🎨",
name:"말랑한 감성 수집가",
color:"민트",
food:"복숭아 아이스크림",
animal:"판다",
mood:"햇살 가득한 정원",
traits:["감성적","유연함","다정함","자유로움"],
description:"평범한 하루에서도 예쁜 순간을 발견하는 감각이 있어요. 자신의 취향과 감정을 소중하게 생각하며 자유롭게 살아가는 편이에요."
},

"INFP":{
emoji:"🌷",
name:"몽글몽글한 이상가",
color:"연보라",
food:"딸기 마카롱",
animal:"토끼",
mood:"꽃이 피어난 들판",
traits:["상상력","공감","진정성","감성"],
description:"마음속에 자신만의 아름다운 세계를 가지고 있어요. 작은 것에도 의미를 발견하고, 자신이 중요하게 생각하는 가치를 소중히 여기는 사람이에요."
},

"INTP":{
emoji:"💡",
name:"호기심 많은 탐구자",
color:"아이스 블루",
food:"민트 초콜릿",
animal:"여우",
mood:"새벽의 연구실",
traits:["호기심","논리적","창의적","분석적"],
description:"'왜?'라는 질문을 좋아하는 타입이에요. 남들이 당연하게 생각하는 것도 한 번 더 파고들며 자신만의 방식으로 답을 찾아가는 편이에요."
},

"ESTP":{
emoji:"⚡",
name:"통통 튀는 행동파",
color:"레몬 옐로우",
food:"레몬 타르트",
animal:"강아지",
mood:"햇살 좋은 축제",
traits:["대담함","활동적","즉흥적","현실적"],
description:"생각만 하기보다 직접 경험하는 것을 좋아해요. 예상하지 못한 상황에서도 빠르게 움직이며 재미있는 순간을 만들어내는 편이에요."
},

"ESFP":{
emoji:"🎀",
name:"반짝이는 분위기 메이커",
color:"코랄 핑크",
food:"딸기 케이크",
animal:"햄스터",
mood:"알록달록한 파티",
traits:["밝음","사교적","감각적","즉흥적"],
description:"어딜 가든 분위기에 생기를 더하는 사람이에요. 사람들과 함께 즐거운 순간을 만드는 것을 좋아하고 현재의 행복을 소중하게 여겨요."
},

"ENFP":{
emoji:"🎈",
name:"아이디어 폭죽",
color:"피치 핑크",
food:"복숭아 소다",
animal:"다람쥐",
mood:"구름 위의 놀이공원",
traits:["열정","창의력","호기심","사교적"],
description:"새로운 것을 발견하면 금세 눈이 반짝이는 타입이에요. 머릿속에서 아이디어가 계속 떠오르고 사람들과 그것을 나누는 것도 좋아해요."
},

"ENTP":{
emoji:"💥",
name:"멈추지 않는 발상 공장",
color:"오렌지",
food:"오렌지 에이드",
animal:"여우",
mood:"아이디어가 폭발하는 작업실",
traits:["재치","호기심","논쟁","창의력"],
description:"남들이 지나치는 곳에서 새로운 가능성을 발견하는 편이에요. 하나의 아이디어에서 또 다른 아이디어를 만들어내는 것을 좋아해요."
},

"ESTJ":{
emoji:"📋",
name:"척척 해내는 총괄대장",
color:"스카이 블루",
food:"소금빵",
animal:"골든리트리버",
mood:"분주한 아침",
traits:["추진력","책임감","현실적","리더십"],
description:"해야 할 일이 생기면 빠르게 정리하고 실행하는 힘이 있어요. 주변 사람들에게 믿음직한 사람으로 보이는 경우가 많아요."
},

"ESFJ":{
emoji:"🍰",
name:"모두의 다정한 친구",
color:"베이비 핑크",
food:"딸기 케이크",
animal:"강아지",
mood:"따뜻한 카페",
traits:["친절함","배려","사교적","협력"],
description:"사람들과 좋은 관계를 만드는 데 자연스러운 재능이 있어요. 주변 사람들이 편안하게 느낄 수 있도록 분위기를 살피는 편이에요."
},

"ENFJ":{
emoji:"🌟",
name:"따뜻한 리더",
color:"골드 크림",
food:"허니 케이크",
animal:"사슴",
mood:"노을이 비치는 광장",
traits:["공감","리더십","열정","배려"],
description:"사람의 가능성을 발견하고 응원하는 힘이 있어요. 혼자 빛나기보다 함께 좋은 방향으로 나아가는 것을 중요하게 생각하는 편이에요."
},

"ENTJ":{
emoji:"🚀",
name:"목표를 향해 가는 지휘자",
color:"라즈베리 레드",
food:"초콜릿 브라우니",
animal:"독수리",
mood:"도시의 야경",
traits:["추진력","전략적","자신감","목표지향"],
description:"목표가 생기면 어떻게 이루어낼지 빠르게 생각하는 타입이에요. 큰 그림을 보고 계획을 세우며 실행으로 옮기는 힘이 있어요."
}

};


/* =========================
   테스트 로직
========================= */

let current = 0;

let scores = {
    E:0, I:0,
    S:0, N:0,
    T:0, F:0,
    J:0, P:0
};


function startTest(){

    current = 0;

    scores = {
        E:0, I:0,
        S:0, N:0,
        T:0, F:0,
        J:0, P:0
    };

    document.getElementById("startScreen").style.display="none";
    document.getElementById("resultScreen").style.display="none";
    document.getElementById("testScreen").style.display="block";

    showQuestion();
}


function showQuestion(){

    const q = questions[current];

    document.getElementById("questionCount").textContent =
        `${current + 1} / ${questions.length}`;

    document.getElementById("questionNumber").textContent =
        `QUESTION ${String(current + 1).padStart(2,"0")}`;

    document.getElementById("question").textContent = q.q;

    document.getElementById("answerA").textContent = "A. " + q.a;
    document.getElementById("answerB").textContent = "B. " + q.b;

    document.getElementById("progress").style.width =
        `${(current / questions.length) * 100}%`;

    if(current < 8){
        document.getElementById("dimension").textContent = "E · I";
    }
    else if(current < 16){
        document.getElementById("dimension").textContent = "S · N";
    }
    else if(current < 24){
        document.getElementById("dimension").textContent = "T · F";
    }
    else{
        document.getElementById("dimension").textContent = "J · P";
    }
}


function selectAnswer(choice){

    const q = questions[current];

    /*
       A를 고르면 해당 질문의 x 방향에 1점.
       B를 고르면 반대 방향에 1점.
    */

    if(choice === 0){
        scores[q.x]++;
    } else {

        const opposite = {
            E:"I", I:"E",
            S:"N", N:"S",
            T:"F", F:"T",
            J:"P", P:"J"
        };

        scores[opposite[q.x]]++;
    }

    current++;

    if(current >= questions.length){
        showResult();
    } else {
        showQuestion();
    }
}


function calculateMBTI(){

    return (
        (scores.E >= scores.I ? "E" : "I") +
        (scores.S >= scores.N ? "S" : "N") +
        (scores.T >= scores.F ? "T" : "F") +
        (scores.J >= scores.P ? "J" : "P")
    );
}


function showResult(){

    const mbti = calculateMBTI();
    const result = results[mbti];

    document.getElementById("testScreen").style.display="none";
    document.getElementById("resultScreen").style.display="block";

    document.getElementById("resultEmoji").textContent=result.emoji;
    document.getElementById("resultType").textContent=mbti;
    document.getElementById("resultName").textContent=result.name;
    document.getElementById("resultDescription").textContent=result.description;

    document.getElementById("resultColor").textContent=result.color;
    document.getElementById("resultFood").textContent=result.food;
    document.getElementById("resultAnimal").textContent=result.animal;
    document.getElementById("resultMood").textContent=result.mood;

    document.getElementById("resultTraits").innerHTML =
        result.traits
        .map(t => `<span class="tag">#${t}</span>`)
        .join("");

    window.scrollTo({
        top:0,
        behavior:"smooth"
    });
}


function restartTest(){

    document.getElementById("resultScreen").style.display="none";
    document.getElementById("startScreen").style.display="flex";

    window.scrollTo({
        top:0,
        behavior:"smooth"
    });
}

</script>

</body>
</html>
```
