# -<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<title>세균 터트리기 게임</title>
<style>
  body {
    margin: 0;
    background: #111;
    color: white;
    font-family: sans-serif;
    text-align: center;
  }

  h1 {
    margin: 10px;
  }

  #score {
    font-size: 20px;
    margin-bottom: 10px;
  }

  .bacteria {
    position: absolute;
    width: 60px;
    height: 60px;
    background: limegreen;
    border-radius: 50%;
    cursor: pointer;
    animation: pop 2s linear forwards;
  }

  @keyframes pop {
    0% { transform: scale(0.5); opacity: 0.5; }
    100% { transform: scale(1); opacity: 1; }
  }
</style>
</head>

<body>

<h1>🧫 세균 터트리기 게임</h1>
<div id="score">점수: 0</div>

<script>
let score = 0;

function createBacteria() {
    const b = document.createElement("div");
    b.className = "bacteria";

    const x = Math.random() * (window.innerWidth - 60);
    const y = Math.random() * (window.innerHeight - 100);

    b.style.left = x + "px";
    b.style.top = y + "px";

    // 클릭하면 터짐
    b.onclick = function() {
        score++;
        document.getElementById("score").innerText = "점수: " + score;
        b.remove();
    };

    document.body.appendChild(b);

    // 2초 후 자동 삭제
    setTimeout(() => {
        b.remove();
    }, 2000);
}

// 계속 생성
setInterval(createBacteria, 500);
</script>

</body>
</html>
