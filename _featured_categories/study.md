---
layout: list
type: category
title: DS Study
slug: study
menu: true
order: 1
description: 데이터 사이언스 및 AI에 관한 학습 내용 기록

---

<div class="subcategory-links">
  <a class="subcategory-link" href="{{ '/ml-dl/' | relative_url }}">
    <div class="subcategory-card">
      <h3>ML/DL</h3>
      <p>머신러닝 및 딥러닝에 관한 학습 내용</p>
    </div>
  </a>
  <a class="subcategory-link" href="{{ '/stats/' | relative_url }}">
    <div class="subcategory-card">
      <h3>Statistics</h3>
      <p>통계학에 관한 학습 내용</p>
    </div>
  </a>
  <a class="subcategory-link" href="{{ '/python/' | relative_url }}">
    <div class="subcategory-card">
      <h3>Python</h3>
      <p>파이썬 프로그래밍에 관한 학습 내용</p>
    </div>
  </a>
</div>

<style>
.subcategory-links {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  justify-content: center;
  margin-top: 2rem;
}

.subcategory-link {
  text-decoration: none; /* 밑줄 제거 */
  color: inherit;
  flex: 1 1 200px;
  max-width: 200px; /* 카드의 최대 크기 설정 */
}

.subcategory-card {
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

.subcategory-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.subcategory-card h3 {
  margin: 0 0 0.5rem;
}

.subcategory-card p {
  margin: 0;
  color: #666;
}
</style>