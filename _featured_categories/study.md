---
layout: list
type: category
title: DS Study
slug: study
menu: true
order: 1
description: 데이터 사이언스 및 AI에 관한 학습 내용 기록

---

<div class="category-links">
  <a class="category-link" href="{{ '/ml/' | relative_url }}">
    <div class="category-card">
      <h3>Machine Learning (ML)</h3>
      <p>머신러닝</p>
    </div>
    <div class="subcategory">
      <a href="{{ '/ml/supervised-learning/' | relative_url }}"><p>Supervised Learning</p></a>
    </div>
  </a>
  <a class="category-link" href="{{ '/dl/' | relative_url }}">
    <div class="category-card">
      <h3>Deep Learning (DL)</h3>
      <p>딥러닝</p>
    </div>
  </a>
  <a class="category-link" href="{{ '/stats/' | relative_url }}">
    <div class="category-card">
      <h3>Statistics</h3>
      <p>통계학</p>
    </div>
  </a>
  <a class="category-link" href="{{ '/python/' | relative_url }}">
    <div class="category-card">
      <h3>Advanced Python</h3>
      <p>고급 파이썬 프로그래밍</p>
    </div>
  </a>
  <a class="category-link" href="{{ '/algorithm/' | relative_url }}">
    <div class="category-card">
      <h3>Data Structures & Algorithm</h3>
      <p>자료구조 및 알고리즘</p>
    </div>
  </a>
  <a class="category-link" href="{{ '/sql/' | relative_url }}">
    <div class="category-card">
      <h3>SQL & Databases</h3>
      <p>SQL 및 데이터베이스</p>
    </div>
  </a>
  <a class="category-link" href="{{ '/nlp/' | relative_url }}">
    <div class="category-card">
      <h3>NLP & LLM</h3>
      <p>자연어 처리 및 거대 언어 모델</p>
    </div>
  </a>
  <a class="category-link" href="{{ '/bi-tools/' | relative_url }}">
    <div class="category-card">
      <h3>Business Intelligence (BI)</h3>
      <p>비즈니스 인텔리전스 도구</p>
    </div>
  </a>
  <a class="category-link" href="{{ '/cloud/' | relative_url }}">
    <div class="category-card">
      <h3>Cloud Computing</h3>
      <p>클라우드 컴퓨팅</p>
    </div>
  </a>
</div>

<style>
.category-links {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  justify-content: center;
  margin-top: 2rem;
}

.category-link {
  position: relative;
  text-decoration: none; /* 밑줄 제거 */
  color: inherit;
  flex: 1 1 200px;
  max-width: 200px; /* 카드의 최대 크기 설정 */
}

.category-card {
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 1rem;
  text-align: center;
  height: 150px;
  transition: transform 0.3s, box-shadow 0.3s;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.category-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.category-card h3 {
  margin: 0 0 0.5rem;
}

.category-card p {
  margin: 0;
  color: #666;
}

/* 숨겨진 상태의 서브 카테고리 */
.subcategory {
  display: none;
  position: absolute;
  top: 100%; /* 상위 요소 아래에 위치 */
  left: 0;
  width: 100%;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 1rem;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  z-index: 10;
}

.category-link:hover .subcategory {
  display: block; /* hover 시 서브카테고리 표시 */
}

.subcategory a {
  text-decoration: none;
  color: inherit;
}

.subcategory p {
  margin: 0.5rem 0;
  color: #666;
  font-size: 0.9rem;
}

</style>