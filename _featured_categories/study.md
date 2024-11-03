---
layout: list
type: category
title: DS Study
slug: study
menu: true
order: 1
description: 데이터 사이언스 및 AI에 관한 학습 내용 기록
---

<div class="mindmap">
  <div class="category" onclick="toggleSubcategories('ml')">
    <h3>Machine Learning (ML)</h3>
    <p>머신러닝</p>
    <div id="ml" class="subcategory hidden">
      <p>Supervised Learning</p>
      <p>Unsupervised Learning</p>
      <p>Reinforcement Learning</p>
      <p>Feature Engineering</p>
    </div>
  </div>

  <div class="category" onclick="toggleSubcategories('dl')">
    <h3>Deep Learning (DL)</h3>
    <p>딥러닝</p>
    <div id="dl" class="subcategory hidden">
      <p>Neural Networks</p>
      <p>Convolutional Neural Networks (CNN)</p>
      <p>Recurrent Neural Networks (RNN)</p>
      <p>Transformers</p>
    </div>
  </div>

  <div class="category" onclick="toggleSubcategories('statistics')">
    <h3>Statistics</h3>
    <p>통계학</p>
    <div id="statistics" class="subcategory hidden">
      <p>Descriptive Statistics</p>
      <p>Inferential Statistics</p>
      <p>Bayesian Analysis</p>
      <p>Hypothesis Testing</p>
    </div>
  </div>

  <div class="category" onclick="toggleSubcategories('python')">
    <h3>Advanced Python</h3>
    <p>고급 파이썬 프로그래밍</p>
    <div id="python" class="subcategory hidden">
      <p>OOP (Object-Oriented Programming)</p>
      <p>Data Handling</p>
      <p>Concurrency</p>
      <p>Performance Optimization</p>
    </div>
  </div>

  <div class="category" onclick="toggleSubcategories('algorithm')">
    <h3>Algorithm</h3>
    <p>자료구조 및 알고리즘</p>
    <div id="algorithm" class="subcategory hidden">
      <p>Sorting & Searching</p>
      <p>Graph Theory</p>
      <p>Dynamic Programming</p>
      <p>Complexity Analysis</p>
    </div>
  </div>

  <div class="category" onclick="toggleSubcategories('sql')">
    <h3>SQL & Databases</h3>
    <p>SQL 및 데이터베이스</p>
    <div id="sql" class="subcategory hidden">
      <p>SQL Queries</p>
      <p>Database Design</p>
      <p>Indexing & Optimization</p>
      <p>NoSQL Databases</p>
    </div>
  </div>

  <!-- 추가된 새로운 카테고리 -->
  <div class="category" onclick="toggleSubcategories('bigdata')">
    <h3>Big Data</h3>
    <p>빅데이터 기술</p>
    <div id="bigdata" class="subcategory hidden">
      <p>Hadoop</p>
      <p>Spark</p>
      <p>Data Lakes</p>
      <p>Data Warehousing</p>
    </div>
  </div>

  <div class="category" onclick="toggleSubcategories('cloud')">
    <h3>Cloud Computing</h3>
    <p>클라우드 컴퓨팅</p>
    <div id="cloud" class="subcategory hidden">
      <p>AWS</p>
      <p>Azure</p>
      <p>Google Cloud</p>
      <p>Serverless Architecture</p>
    </div>
  </div>

  <div class="category" onclick="toggleSubcategories('bi')">
    <h3>Business Intelligence (BI)</h3>
    <p>비즈니스 인텔리전스 도구</p>
    <div id="bi" class="subcategory hidden">
      <p>Power BI</p>
      <p>Tableau</p>
      <p>Data Visualization</p>
      <p>Data Storytelling</p>
    </div>
  </div>

  <div class="category" onclick="toggleSubcategories('nlp')">
    <h3>Natural Language Processing (NLP)</h3>
    <p>자연어 처리</p>
    <div id="nlp" class="subcategory hidden">
      <p>Tokenization</p>
      <p>Sentiment Analysis</p>
      <p>Named Entity Recognition (NER)</p>
      <p>Language Models</p>
    </div>
  </div>

</div>

<style>
.mindmap {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  justify-content: center;
  margin-top: 2rem;
}

.category {
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 1rem;
  text-align: center;
  width: 200px;
  cursor: pointer;
  transition: transform 0.3s, box-shadow 0.3s;
}

.category:hover {
  transform: translateY(-5px);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.subcategory {
  margin-top: 1rem;
}

.subcategory.hidden {
  display: none;
}

.subcategory p {
  margin: 0.5rem 0;
  color: #666;
  font-size: 0.9rem;
}
</style>

<script>
function toggleSubcategories(id) {
  const subcategory = document.getElementById(id);
  subcategory.classList.toggle("hidden");
}
</script>