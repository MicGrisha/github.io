<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Вопросы для чиловой катки</title>
<style>
body {
  margin: 0;
  font-family: 'Georgia', serif;
  color: #f5f1e6;
  background: url('google_form_background.png') no-repeat center center fixed;
  background-size: cover;
}

.overlay {
  background: rgba(20, 15, 10, 0.75);
  min-height: 100vh;
  padding: 40px 20px;
}

.container {
  max-width: 700px;
  margin: auto;
  background: rgba(30, 20, 15, 0.85);
  padding: 30px;
  border-radius: 12px;
  box-shadow: 0 0 20px rgba(0,0,0,0.7);
}

h1 {
  text-align: center;
  margin-bottom: 10px;
}

p.description {
  text-align: center;
  font-size: 14px;
  opacity: 0.8;
}

label {
  display: block;
  margin-top: 20px;
  font-weight: bold;
}

input, textarea, select {
  width: 100%;
  margin-top: 5px;
  padding: 10px;
  border-radius: 6px;
  border: none;
  background: rgba(255,255,255,0.1);
  color: #fff;
}

button {
  margin-top: 25px;
  width: 100%;
  padding: 12px;
  border: none;
  border-radius: 8px;
  background: #c9a66b;
  color: #1a120d;
  font-weight: bold;
  cursor: pointer;
}

button:hover {
  background: #e0c48a;
}
</style>
</head>
<body>
<div class="overlay">
  <div class="container">
    <h1>📜 Досье допуска</h1>
    <p class="description">Ответьте честно — некоторые истины лучше не скрывать</p>

    <form>
      <label>1. Чего вы ждете от игры?</label>
      <textarea rows="3"></textarea>

      <label>2. Есть ли темы, которые не стоит затрагивать?</label>
      <textarea rows="3"></textarea>

      <label>3. Соотношение боев/социалки (%)</label>
      <input type="text" placeholder="60/40">

      <label>4. Нужна ли помощь с персонажем?</label>
      <select>
        <option>Да</option>
        <option>Частично</option>
        <option>Нет</option>
        <option>Хочу готового</option>
      </select>

      <label>5. Насколько серьёзной должна быть игра?</label>
      <input type="range" min="1" max="5">

      <label>6. Отношение к риску смерти персонажа</label>
      <select>
        <option>Нормально</option>
        <option>Допустимо</option>
        <option>Минимальный риск</option>
        <option>Не хочу</option>
      </select>

      <label>7. Что хотите попробовать в игре?</label>
      <textarea rows="3"></textarea>

      <button type="submit">Отправить</button>
    </form>

<script>
const scriptURL = 'https://script.google.com/macros/s/AKfycbwBKnnNJwcmTqZfe9PBLIANR50Hj8Qeu8b0KYdpqB-uxA7kcRUJ9faJHbZpnKXrpk16UA/exec';
const form = document.querySelector('form');

form.addEventListener('submit', e => {
  e.preventDefault();

  const data = {
    q1: form[0].value,
    q2: form[1].value,
    q3: form[2].value,
    q4: form[3].value,
    q5: form[4].value,
    q6: form[5].value,
    q7: form[6].value
  };

  fetch(scriptURL, {
    method: 'POST',
    body: JSON.stringify(data),
    headers: { 'Content-Type': 'application/json' }
  })
  .then(() => {
    alert('Ответы отправлены в Архив');
    form.reset();
  })
  .catch(error => alert('Ошибка: ' + error.message));
});
</script>
  </div>
</div>
</body>
</html>
