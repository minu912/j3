<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>일본어 단어 퀴즈</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      padding: 40px;
    }
    h1 {
      font-size: 2rem;
    }
    .word {
      font-size: 2rem;
      margin: 20px;
    }
    input, button {
      font-size: 1.2rem;
      padding: 10px;
      margin: 10px;
    }
    .result {
      font-size: 1.2rem;
      margin-top: 20px;
    }
    .question-number {
      font-size: 1rem;
      margin-top: 10px;
    }
  </style>
</head>
<body>
  <h1>일본어 단어 퀴즈</h1>
  <div class="question-number" id="questionNumber"></div>
  <div class="word" id="question"></div>
  <input type="text" id="answer" placeholder="발음을 입력하세요" />
  <div>
    <button onclick="checkAnswer()">정답 확인</button>
    <button onclick="restartQuiz()">다시 시작</button>
  </div>
  <div class="result" id="result"></div>

  <script>
    const wordList = {
     "필요": "히쓰요",
"실례": "시쓰레-",
"예약": "요야쿠",
"동물원": "도-부츠츠엔",
"개인": "코진",
"시험": "시켄",
"반지": "유비와",
"역사": "레키시",
"빛": "히카리",
"세탁": "센타쿠",
"목숨, 생명": "이노치",
"운전": "운뗀",
"졸업": "소츠교-",
"힘들다, 큰일": "타이헨",
"주차": "추-샤",
"교차점, 사거리": "코-사텐",
"용건, 볼일": "요-지",
"맞은편, 건너편": "무코-",
"저녁, 저녁밥": "유-쇼쿠",
"덕분": "오카게",
"입원": "뉴-잉",
"퇴원": "타이잉",
"수업": "주교-",
"대부분, 거의": "호톤도",
"숲": "모리",
"도둑": "도로보-",
"방송": "호-소-",
"벌레": "무시",
"수영": "수이에-",
"상자": "하코",
"복도": "로-까",
"전쟁": "센소-",
"마음": "코코로",
"서투름": "헤타",
"배 (선박)": "후네",
"미술관": "비쥬추깡",
"회의": "카이기",
"생선, 물고기": "사카나",
"달걀, 알": "타마고",
"선수": "센슈",
"비누": "셋켄",
"목/목구멍": "노도",
"손수건/수건": "한카치",
"전철": "뎅샤",
"출구": "데구치",
"휴식, 쉬는 날": "야스미",
"가게, 상점": "미세",
"앞": "마에",
"공부": "벤교-",
"번호": "방고-",
    };

    const koreanWords = Object.keys(wordList);
    let currentIndex = 0;
    let correctCount = 0;
    let isAnswered = false;

    function showQuestion() {
      if (currentIndex < koreanWords.length) {
        document.getElementById('question').textContent = koreanWords[currentIndex];
        document.getElementById('questionNumber').textContent = `${currentIndex + 1} / ${koreanWords.length}`;
        document.getElementById('answer').value = "";
        document.getElementById('result').textContent = "";
        isAnswered = false;
      } else {
        showResult();
      }
    }

    function checkAnswer() {
      if (isAnswered) return;
      const userAnswer = document.getElementById('answer').value.trim();
      const correctAnswer = wordList[koreanWords[currentIndex]];
      const resultDiv = document.getElementById('result');
      if (userAnswer === correctAnswer) {
        resultDiv.textContent = "정답입니다!";
        resultDiv.style.color = "blue";
        correctCount++;
      } else {
        resultDiv.textContent = `틀렸습니다. 정답은 '${correctAnswer}'입니다.`;
        resultDiv.style.color = "red";
      }
      isAnswered = true;
      setTimeout(() => {
        currentIndex++;
        showQuestion();
      }, 2000);
    }

    function restartQuiz() {
      currentIndex = 0;
      correctCount = 0;
      showQuestion();
    }

    function showResult() {
      alert(`퀴즈 종료!\n맞춘 개수: ${correctCount} / ${koreanWords.length}\n점수: ${correctCount}점`);
      restartQuiz();
    }

    showQuestion();
  </script>
</body>
</html>

