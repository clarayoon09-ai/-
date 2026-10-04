<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>너진똑 판다 옷 입히기 🐼</title>

<style>
@import url('https://fonts.googleapis.com/css2?family=Jua&family=Noto+Sans+KR:wght@400;700&display=swap');

* {
    box-sizing: border-box;
}

body {
    margin: 0;
    min-height: 100vh;
    font-family: 'Noto Sans KR', sans-serif;
    background: #fff7f1;
    color: #443b38;
}

button {
    font-family: inherit;
    cursor: pointer;
}

.header {
    text-align: center;
    padding: 28px 15px 15px;
}

.header h1 {
    margin: 0;
    font-family: 'Jua', sans-serif;
    font-size: 38px;
    color: #5c4b46;
}

.header p {
    margin: 8px 0 0;
    color: #8d7d77;
}

.game {
    width: min(1100px, 94%);
    margin: 15px auto 40px;
    display: grid;
    grid-template-columns: 1fr 390px;
    gap: 25px;
}

/* =========================
   판다 화면
========================= */

.preview {
    min-height: 650px;
    border-radius: 30px;
    background: linear-gradient(135deg, #fffdf9, #f8f0ff);
    box-shadow: 0 10px 30px rgba(80,60,60,.10);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    position: relative;
    overflow: hidden;
    transition: background .3s;
}

.preview-title {
    position: absolute;
    top: 20px;
    left: 25px;
    font-family: 'Jua', sans-serif;
    font-size: 22px;
}

.scene {
    width: 330px;
    height: 450px;
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
}

/* =========================
   기본 판다
========================= */

.panda {
    position: relative;
    width: 230px;
    height: 350px;
}

/* 귀 */

.ear {
    position: absolute;
    width: 68px;
    height: 68px;
    border-radius: 50%;
    background: #292727;
    top: 32px;
    z-index: 1;
}

.ear.left {
    left: 22px;
}

.ear.right {
    right: 22px;
}

/* 몸 */

.body {
    position: absolute;
    width: 145px;
    height: 150px;
    background: #292727;
    border-radius: 60px 60px 45px 45px;
    left: 42px;
    bottom: 25px;
}

/* 얼굴 */

.face {
    position: absolute;
    width: 190px;
    height: 190px;
    border-radius: 50%;
    background: white;
    border: 5px solid #292727;
    left: 20px;
    top: 45px;
    z-index: 3;
}

/* 눈 */

.eye {
    position: absolute;
    width: 23px;
    height: 29px;
    background: #181818;
    border-radius: 50%;
    top: 68px;
}

.eye.left {
    left: 43px;
}

.eye.right {
    right: 43px;
}

/* 큰 동그란 눈 포인트 */

.eye-ring {
    position: absolute;
    width: 42px;
    height: 42px;
    border: 5px solid #181818;
    border-radius: 50%;
    right: 32px;
    top: 61px;
    background: white;
}

.eye-ring::after {
    content: "";
    position: absolute;
    width: 17px;
    height: 22px;
    background: #181818;
    border-radius: 50%;
    left: 7px;
    top: 7px;
}

/* 볼 */

.cheek {
    position: absolute;
    width: 42px;
    height: 27px;
    background: #ffb9bf;
    border-radius: 50%;
    top: 116px;
    opacity: .75;
}

.cheek.left {
    left: 20px;
}

.cheek.right {
    right: 20px;
}

/* 입 */

.mouth {
    position: absolute;
    left: 82px;
    top: 116px;
    font-size: 25px;
    font-weight: bold;
}

/* =========================
   옷
========================= */

.clothes {
    position: absolute;
    left: 47px;
    bottom: 33px;
    width: 136px;
    height: 120px;
    z-index: 4;
    border-radius: 45px 45px 30px 30px;
    background: #8db9d8;
    border: 4px solid #292727;
}

/* 옷별 스타일 */

.clothes.school {
    background: #526f91;
}

.clothes.maid {
    background: #303030;
}

.clothes.princess {
    background: #f29bb0;
}

.clothes.hoodie {
    background: #77b9d5;
}

.clothes.suit {
    background: #252936;
}

.clothes.hanbok {
    background: #f3b1bd;
}

/* 옷 단추 */

.clothes::after {
    content: "•  •  •";
    position: absolute;
    left: 37px;
    top: 35px;
    color: white;
    font-size: 18px;
}

/* =========================
   모자
========================= */

.hat {
    position: absolute;
    z-index: 8;
    left: 50%;
    transform: translateX(-50%);
    top: 18px;
    font-size: 70px;
    line-height: 1;
    display: none;
}

.hat.show {
    display: block;
}

/* =========================
   액세서리
========================= */

.accessory {
    position: absolute;
    z-index: 10;
    left: 50%;
    transform: translateX(-50%);
    top: 128px;
    font-size: 45px;
    display: none;
}

.accessory.show {
    display: block;
}

/* =========================
   소품
========================= */

.prop {
    position: absolute;
    z-index: 11;
    right: 0;
    bottom: 55px;
    font-size: 65px;
    display: none;
}

.prop.show {
    display: block;
}

/* =========================
   옷장
========================= */

.wardrobe {
    background: white;
    border-radius: 30px;
    padding: 20px;
    box-shadow: 0 10px 30px rgba(80,60,60,.10);
    max-height: 700px;
    overflow-y: auto;
}

.tabs {
    display: flex;
    gap: 7px;
    overflow-x: auto;
    padding-bottom: 10px;
}

.tab {
    flex-shrink: 0;
    border: none;
    background: #f2eeee;
    padding: 10px 15px;
    border-radius: 15px;
    font-size: 14px;
}

.tab.active {
    background: #5d504b;
    color: white;
}

.items {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 10px;
}

.item {
    border: 2px solid #eee7e4;
    background: #fffaf8;
    border-radius: 18px;
    padding: 12px 5px;
    min-height: 100px;
    transition: .2s;
}

.item:hover {
    transform: translateY(-3px);
    border-color: #d7b9b0;
}

.item.selected {
    border-color: #74605a;
    background: #f8efec;
}

.item-icon {
    font-size: 37px;
    display: block;
    margin-bottom: 5px;
}

.item-name {
    font-size: 12px;
}

/* 버튼 */

.actions {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 10px;
    margin-top: 18px;
}

.action {
    border: none;
    padding: 13px;
    border-radius: 15px;
    background: #eee7e3;
    font-weight: bold;
}

.action.random {
    background: #81706a;
    color: white;
}

.action.save {
    background: #e9a5b3;
    color: white;
}

.current {
    margin-top: 15px;
    padding: 12px;
    background: #faf6f3;
    border-radius: 15px;
    font-size: 13px;
    line-height: 1.7;
}

/* =========================
   모바일
========================= */

@media (max-width: 800px) {

    .header h1 {
        font-size: 30px;
    }

    .game {
        grid-template-columns: 1fr;
    }

    .preview {
        min-height: 540px;
    }

    .wardrobe {
        max-height: none;
    }

    .scene {
        transform: scale(.9);
    }
}

@media (max-width: 420px) {

    .scene {
        transform: scale(.75);
    }

    .items {
        grid-template-columns: repeat(3, 1fr);
    }
}
</style>
</head>

<body>

<header class="header">
    <h1>🐼 너진똑 판다 옷 입히기</h1>
    <p>귀여운 너진똑에게 마음대로 코디를 입혀보세요!</p>
</header>

<main class="game">

    <!-- =========================
         판다 미리보기
    ========================= -->

    <section class="preview" id="preview">

        <div class="preview-title">
            ✨ 나만의 너진똑
        </div>

        <div class="scene">

            <div class="panda" id="panda">

                <div class="ear left"></div>
                <div class="ear right"></div>

                <div class="body"></div>

                <div class="face">

                    <div class="eye left"></div>

                    <div class="eye-ring"></div>

                    <div class="cheek left"></div>
                    <div class="cheek right"></div>

                    <div class="mouth">ᴗ</div>

                </div>

                <!-- 옷 -->
                <div class="clothes" id="clothes"></div>

                <!-- 모자 -->
                <div class="hat" id="hat"></div>

                <!-- 액세서리 -->
                <div class="accessory" id="accessory"></div>

                <!-- 소품 -->
                <div class="prop" id="prop"></div>

            </div>

        </div>

    </section>


    <!-- =========================
         옷장
    ========================= -->

    <section class="wardrobe">

        <div class="tabs">

            <button class="tab active" onclick="openCategory('clothes', this)">
                👗 옷
            </button>

            <button class="tab" onclick="openCategory('hat', this)">
                🎩 모자
            </button>

            <button class="tab" onclick="openCategory('accessory', this)">
                🎀 장식
            </button>

            <button class="tab" onclick="openCategory('prop', this)">
                👜 소품
            </button>

            <button class="tab" onclick="openCategory('background', this)">
                🌈 배경
            </button>

        </div>

        <div class="items" id="items"></div>

        <div class="actions">

            <button class="action random" onclick="randomOutfit()">
                🎲 랜덤 코디
            </button>

            <button class="action" onclick="resetOutfit()">
                🔄 초기화
            </button>

            <button class="action save" onclick="saveOutfit()">
                📸 저장하기
            </button>

        </div>

        <div class="current" id="current">
            현재 코디: 기본 너진똑
        </div>

    </section>

</main>


<script>

/* =====================================================
   옷 데이터
===================================================== */

const wardrobe = {

    clothes: [

        {
            name: "기본",
            icon: "🤍",
            value: "default"
        },

        {
            name: "교복",
            icon: "🎒",
            value: "school"
        },

        {
            name: "메이드복",
            icon: "🖤",
            value: "maid"
        },

        {
            name: "공주 드레스",
            icon: "👗",
            value: "princess"
        },

        {
            name: "후드티",
            icon: "🩵",
            value: "hoodie"
        },

        {
            name: "정장",
            icon: "🕴️",
            value: "suit"
        },

        {
            name: "한복",
            icon: "🌸",
            value: "hanbok"
        }

    ],


    hat: [

        {
            name: "없음",
            icon: "🚫",
            value: ""
        },

        {
            name: "왕관",
            icon: "👑",
            value: "👑"
        },

        {
            name: "리본",
            icon: "🎀",
            value: "🎀"
        },

        {
            name: "꽃",
            icon: "🌸",
            value: "🌸"
        },

        {
            name: "베레모",
            icon: "🧢",
            value: "🧢"
        },

        {
            name: "마법사 모자",
            icon: "🧙",
            value: "🧙"
        },

        {
            name: "경찰 모자",
            icon: "👮",
            value: "👮"
        }

    ],


    accessory: [

        {
            name: "없음",
            icon: "🚫",
            value: ""
        },

        {
            name: "하트 안경",
            icon: "🕶️",
            value: "💗"
        },

        {
            name: "안경",
            icon: "👓",
            value: "👓"
        },

        {
            name: "별",
            icon: "⭐",
            value: "⭐"
        },

        {
            name: "꽃",
            icon: "🌼",
            value: "🌼"
        },

        {
            name: "반짝이",
            icon: "✨",
            value: "✨"
        }

    ],


    prop: [

        {
            name: "없음",
            icon: "🚫",
            value: ""
        },

        {
            name: "책",
            icon: "📖",
            value: "📖"
        },

        {
            name: "카메라",
            icon: "📷",
            value: "📷"
        },

        {
            name: "음료",
            icon: "🧋",
            value: "🧋"
        },

        {
            name: "꽃다발",
            icon: "💐",
            value: "💐"
        },

        {
            name: "노트북",
            icon: "💻",
            value: "💻"
        },

        {
            name: "가방",
            icon: "🎒",
            value: "🎒"
        }

    ],


    background: [

        {
            name: "기본",
            icon: "🤍",
            value: "default"
        },

        {
            name: "하늘",
            icon: "☁️",
            value: "sky"
        },

        {
            name: "핑크",
            icon: "🌸",
            value: "pink"
        },

        {
            name: "숲",
            icon: "🌳",
            value: "forest"
        },

        {
            name: "바다",
            icon: "🌊",
            value: "sea"
        },

        {
            name: "밤",
            icon: "🌙",
            value: "night"
        }

    ]

};


/* =====================================================
   현재 코디
===================================================== */

let outfit = {

    clothes: "default",

    hat: "",

    accessory: "",

    prop: "",

    background: "default"

};


/* =====================================================
   카테고리 열기
===================================================== */

function openCategory(category, button) {

    document.querySelectorAll(".tab").forEach(tab => {
        tab.classList.remove("active");
    });

    button.classList.add("active");

    const container = document.getElementById("items");

    container.innerHTML = "";

    wardrobe[category].forEach(item => {

        const div = document.createElement("button");

        div.className = "item";

        div.innerHTML = `
            <span class="item-icon">${item.icon}</span>
            <span class="item-name">${item.name}</span>
        `;

        if (outfit[category] === item.value) {
            div.classList.add("selected");
        }

        div.onclick = () => {

            outfit[category] = item.value;

            applyOutfit();

            openCategory(category, button);

        };

        container.appendChild(div);

    });

}


/* =====================================================
   코디 적용
===================================================== */

function applyOutfit() {

    const clothes = document.getElementById("clothes");
    const hat = document.getElementById("hat");
    const accessory = document.getElementById("accessory");
    const prop = document.getElementById("prop");
    const preview = document.getElementById("preview");


    /* 옷 */

    clothes.className = "clothes";

    if (outfit.clothes !== "default") {

        clothes.classList.add(outfit.clothes);

    }


    /* 모자 */

    hat.innerHTML = outfit.hat;

    if (outfit.hat) {

        hat.classList.add("show");

    } else {

        hat.classList.remove("show");

    }


    /* 장식 */

    accessory.innerHTML = outfit.accessory;

    if (outfit.accessory) {

        accessory.classList.add("show");

    } else {

        accessory.classList.remove("show");

    }


    /* 소품 */

    prop.innerHTML = outfit.prop;

    if (outfit.prop) {

        prop.classList.add("show");

    } else {

        prop.classList.remove("show");

    }


    /* 배경 */

    const backgrounds = {

        default:
            "linear-gradient(135deg,#fffdf9,#f8f0ff)",

        sky:
            "linear-gradient(135deg,#dff4ff,#f5fbff)",

        pink:
            "linear-gradient(135deg,#ffe3ec,#fff4f7)",

        forest:
            "linear-gradient(135deg,#dcefdc,#f5f8e9)",

        sea:
            "linear-gradient(135deg,#d8f5f4,#eafcff)",

        night:
            "linear-gradient(135deg,#292b50,#514d79)"

    };

    preview.style.background =
        backgrounds[outfit.background];


    updateCurrent();

}


/* =====================================================
   현재 코디 글자
===================================================== */

function findName(category, value) {

    const item = wardrobe[category].find(
        x => x.value === value
    );

    return item ? item.name : "없음";

}


function updateCurrent() {

    const text = document.getElementById("current");

    text.innerHTML = `
        <b>현재 코디</b><br>
        👗 ${findName("clothes", outfit.clothes)}　
        🎩 ${findName("hat", outfit.hat)}<br>
        🎀 ${findName("accessory", outfit.accessory)}　
        👜 ${findName("prop", outfit.prop)}<br>
        🌈 ${findName("background", outfit.background)}
    `;

}


/* =====================================================
   랜덤 코디
===================================================== */

function randomOutfit() {

    Object.keys(wardrobe).forEach(category => {

        const list = wardrobe[category];

        const random =
            list[Math.floor(Math.random() * list.length)];

        outfit[category] = random.value;

    });

    applyOutfit();

}


/* =====================================================
   초기화
===================================================== */

function resetOutfit() {

    outfit = {

        clothes: "default",

        hat: "",

        accessory: "",

        prop: "",

        background: "default"

    };

    applyOutfit();

}


/* =====================================================
   PNG 저장
===================================================== */

function saveOutfit() {

    alert(
        "현재 버전에서는 브라우저 화면 저장 기능을 준비 중이에요! 🐼\n\n" +
        "휴대폰이라면 스크린샷으로 저장할 수도 있어요."
    );

}


/* =====================================================
   처음 실행
===================================================== */

openCategory(
    "clothes",
    document.querySelector(".tab")
);

applyOutfit();

</script>

</body>
</html>
