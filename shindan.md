---
layout: page
title: AIツール診断
permalink: /shindan/
---

<p style="font-size:0.85em;color:#666;border:1px solid #ddd;padding:0.4em 0.8em;border-radius:6px;">※本ページはプロモーション（広告）を含みます。</p>

<p>やりたいことを選ぶだけで、あなたに合いそうなAIツールやガジェットと、参考になる記事を紹介します。</p>

<div id="shindan-app">
  <fieldset>
    <legend>AIでやりたいことは？</legend>
    <label><input type="radio" name="purpose" value="write"> 文章・SEO記事を書きたい</label><br>
    <label><input type="radio" name="purpose" value="image"> 画像を作りたい</label><br>
    <label><input type="radio" name="purpose" value="memo"> 議事録・資料をまとめたい</label><br>
    <label><input type="radio" name="purpose" value="chat"> 何でも相談できる汎用AIが欲しい</label>
  </fieldset>
  <fieldset>
    <legend>作業環境・ゲームのこと</legend>
    <label><input type="radio" name="purpose" value="mic"> 会議の録音・音質を良くしたい</label><br>
    <label><input type="radio" name="purpose" value="desk"> 在宅の作業環境を整えたい</label><br>
    <label><input type="radio" name="purpose" value="valo"> VALORANTを快適に遊びたい・上達したい</label>
  </fieldset>
  <button id="shindan-btn" type="button">診断する</button>
  <div id="shindan-result"></div>
</div>

<style>
#shindan-app { max-width: 560px; margin-top: 1.5em; }
#shindan-app fieldset { border: 1px solid #ddd; border-radius: 8px; padding: 1em 1.2em; margin-bottom: 1em; }
#shindan-app label { display: inline-block; margin: 0.3em 0; }
#shindan-btn {
  padding: 0.6em 1.4em; font-size: 1em;
  background: #2a7ae2; color: #fff; border: none; border-radius: 6px; cursor: pointer;
}
#shindan-btn:hover { background: #1f5fb8; }
#shindan-result {
  margin-top: 1.2em; padding: 1em 1.2em; border-radius: 8px;
  background: #f4f7fb; border: 1px solid #dbe6f5; display: none;
}
#shindan-result.show { display: block; }
#shindan-result .rec a { font-weight: bold; }
#shindan-result ul { margin-bottom: 0; }
</style>

<script>
(function () {
  var recommendations = {
    write: {
      name: "Value AI Writer",
      reason: "AIでSEO記事を高速生成できるツールです。文章作成・ブログ運営の効率化に向いています。",
      url: "https://px.a8.net/svt/ejp?a8mat=4BC9F3+F75DPU+1JUK+1HNDBM",
      sponsored: true,
      articles: [
        ["AI記事作成ツールの選び方", "{% post_url 2026-09-12-ai-kijisakusei-hikaku %}"]
      ]
    },
    image: {
      name: "ConoHa AI Canvas",
      reason: "ブラウザだけで、インストール不要で本格的なAI画像生成ができます。",
      url: "https://px.a8.net/svt/ejp?a8mat=4BC9F3+FA4JQQ+50+7RU5R6",
      sponsored: true,
      articles: [
        ["AI画像生成ツールの選び方", "{% post_url 2026-09-12-ai-gazou-seisei-hikaku %}"],
        ["AIで作った画像は商用利用できる？", "{% post_url 2026-09-28-ai-gazou-shouyou %}"]
      ]
    },
    memo: {
      name: "Notta Brain",
      reason: "会議の議事録や資料作成を自動で整理・要約してくれるAIエージェントです。",
      url: "https://px.a8.net/svt/ejp?a8mat=4BC9F3+F8C8XE+5988+HVFKY",
      sponsored: true,
      articles: [
        ["AI議事録・文字起こしツールの選び方", "{% post_url 2026-09-12-ai-gijiroku-hikaku %}"],
        ["会議の議事録をAIで自動化する方法", "{% post_url 2026-09-28-ai-gijiroku-jidouka %}"]
      ]
    },
    chat: {
      name: "ChatGPT / Claude / Gemini の比較記事",
      reason: "用途に応じた選び方は、こちらの比較記事で詳しく解説しています。",
      url: "{% post_url 2026-09-11-chatgpt-claude-gemini-hikaku %}",
      articles: [
        ["無料で使えるAIツールまとめ", "{% post_url 2026-09-12-ai-muryou-matome %}"]
      ]
    },
    mic: {
      name: "AI議事録の精度を上げるマイクの選び方",
      reason: "AI議事録の精度は、録音の音質で大きく変わります。会議の人数や場所に合ったマイクを選びましょう。",
      url: "{% post_url 2026-09-28-gijiroku-mic-erabikata %}",
      articles: [
        ["会議の議事録をAIで自動化する方法", "{% post_url 2026-09-28-ai-gijiroku-jidouka %}"]
      ]
    },
    desk: {
      name: "在宅でAIを使う人の作業がはかどるガジェット4選",
      reason: "モニター・キーボード・イヤホン・PCスタンドで、AIを使った作業がぐっと快適になります。",
      url: "{% post_url 2026-09-28-zaitaku-ai-gadget %}",
      articles: []
    },
    valo: {
      name: "VALORANT向けゲーミングマウスの選び方",
      reason: "エイムの安定感はマウスで大きく変わります。まずはマウスから見直すのがおすすめです。",
      url: "https://lucky7ky.github.io/game/valorant/valorant-mouse/",
      articles: [
        ["VALORANT向けゲーミングモニターの選び方", "https://lucky7ky.github.io/game/valorant/valorant-monitor/"],
        ["足音を聞き取りやすいヘッドセット・イヤホンの選び方", "https://lucky7ky.github.io/game/valorant/valorant-headset/"],
        ["VALORANTを快適に遊ぶためのPC選び", "https://lucky7ky.github.io/game/valorant/valorant-pc/"],
        ["イモータルのイニシエーター専が解説｜ソーヴァ・スカイ・フェイド", "https://lucky7ky.github.io/game/valorant/valorant-initiator/"],
        ["感度は低すぎ？プロ646人の統計と比較（計算ツール付き）", "https://lucky7ky.github.io/game/valorant/valorant-kando-hikaku/"]
      ]
    }
  };

  document.getElementById("shindan-btn").addEventListener("click", function () {
    var checked = document.querySelector('input[name="purpose"]:checked');
    var resultEl = document.getElementById("shindan-result");
    if (!checked) {
      resultEl.innerHTML = "まずは1つ選んでください。";
      resultEl.classList.add("show");
      return;
    }
    var rec = recommendations[checked.value];
    var link = rec.sponsored
      ? "<a href=\"" + rec.url + "\" target=\"_blank\" rel=\"nofollow sponsored noopener\">" + rec.name + "</a>"
      : "<a href=\"" + rec.url + "\">" + rec.name + "</a>";
    var html = "<p class=\"rec\">おすすめは " + link + " です。</p><p>" + rec.reason + "</p>";
    if (rec.articles.length) {
      html += "<p>あわせて読みたい記事：</p><ul>";
      for (var i = 0; i < rec.articles.length; i++) {
        html += "<li><a href=\"" + rec.articles[i][1] + "\">" + rec.articles[i][0] + "</a></li>";
      }
      html += "</ul>";
    }
    resultEl.innerHTML = html;
    resultEl.classList.add("show");
  });
})();
</script>
