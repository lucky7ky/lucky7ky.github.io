---
layout: page
title: AIツール診断
permalink: /shindan/
---

<p>やりたいことを選ぶだけで、あなたに合いそうなAIツールを診断します。</p>

<div id="shindan-app">
  <fieldset>
    <legend>主な用途はどれですか？</legend>
    <label><input type="radio" name="purpose" value="write"> 文章・SEO記事を書きたい</label><br>
    <label><input type="radio" name="purpose" value="image"> 画像を作りたい</label><br>
    <label><input type="radio" name="purpose" value="memo"> 議事録・資料をまとめたい</label><br>
    <label><input type="radio" name="purpose" value="chat"> 何でも相談できる汎用AIが欲しい</label>
  </fieldset>
  <button id="shindan-btn" type="button">診断する</button>
  <div id="shindan-result"></div>
</div>

<style>
#shindan-app { max-width: 560px; margin-top: 1.5em; }
#shindan-app fieldset { border: 1px solid #ddd; border-radius: 8px; padding: 1em 1.2em; }
#shindan-app label { display: inline-block; margin: 0.3em 0; }
#shindan-btn {
  margin-top: 1em; padding: 0.6em 1.4em; font-size: 1em;
  background: #2a7ae2; color: #fff; border: none; border-radius: 6px; cursor: pointer;
}
#shindan-btn:hover { background: #1f5fb8; }
#shindan-result {
  margin-top: 1.2em; padding: 1em 1.2em; border-radius: 8px;
  background: #f4f7fb; border: 1px solid #dbe6f5; display: none;
}
#shindan-result.show { display: block; }
#shindan-result a { font-weight: bold; }
</style>

<script>
(function () {
  var recommendations = {
    write: {
      name: "Value AI Writer",
      reason: "AIでSEO記事を高速生成できるツールです。文章作成・ブログ運営の効率化に向いています。",
      url: "https://www.value-press.com/"
    },
    image: {
      name: "ConoHa AI Canvas",
      reason: "ブラウザだけで、インストール不要で本格的なAI画像生成ができます。",
      url: "https://ai.conoha.jp/"
    },
    memo: {
      name: "Notta Brain",
      reason: "会議の議事録や資料作成を自動で整理・要約してくれるAIエージェントです。",
      url: "https://notta.ai/"
    },
    chat: {
      name: "ChatGPT / Claude / Gemini の比較記事",
      reason: "用途に応じた選び方は、こちらの比較記事で詳しく解説しています。",
      url: "/2026/09/11/chatgpt-claude-gemini-hikaku.html"
    }
  };

  document.getElementById("shindan-btn").addEventListener("click", function () {
    var checked = document.querySelector('input[name="purpose"]:checked');
    var resultEl = document.getElementById("shindan-result");
    if (!checked) {
      resultEl.innerHTML = "まずは用途を1つ選んでください。";
      resultEl.classList.add("show");
      return;
    }
    var rec = recommendations[checked.value];
    resultEl.innerHTML =
      "<p>おすすめは <a href=\"" + rec.url + "\" target=\"_blank\" rel=\"noopener\">" + rec.name + "</a> です。</p>" +
      "<p>" + rec.reason + "</p>";
    resultEl.classList.add("show");
  });
})();
</script>
