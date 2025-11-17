<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Stress And Anxiety</title>

<!-- Fuentes -->
<link href="https://fonts.googleapis.com/css2?family=PT+Serif:wght@400;700&family=Inter:wght@300;400;700&display=swap" rel="stylesheet">

<style>
/* RESET */
* {
  margin: 0; padding: 0; box-sizing: border-box;
}
body {
  font-family: "Inter", sans-serif;
  background: #fff;
  color: #333;
  line-height: 1.6;
}

/* CONTENEDOR */
.container {
  width: 90%;
  max-width: 1100px;
  margin: auto;
  padding: 20px 0;
}

/* TITULOS */
.section-title {
  font-family: "PT Serif", serif;
  font-size: 42px;
  margin-bottom: 10px;
}
.section-sub {
  text-transform: uppercase;
  font-size: 14px;
  opacity: .6;
}

/* TEXTO */
p {
  margin-top: 10px;
  font-size: 17px;
}

/* IMAGENES */
.img {
  width: 100%;
  border-radius: 12px;
  margin: 20px 0;
}

/* --- STORIES SLIDER --- */
.slider {
  width: 100%;
  max-width: 900px;
  height: 500px;
  position: relative;
  overflow: hidden;
  border-radius: 15px;
  box-shadow: 0 4px 20px rgba(0,0,0,0.3);
  margin: 40px auto;
}
.slide {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  left: 100%;
  opacity: 0;
  transition: all 1s ease;
  display: flex;
  background: #fff;
}
.slide.active {
  left: 0;
  opacity: 1;
}
.slide img {
  width: 50%;
  object-fit: cover;
}
.text {
  width: 50%;
  padding: 30px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

/* DOTS */
.dots {
  position: absolute;
  bottom: 15px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  gap: 10px;
}
.dot {
  width: 12px;
  height: 12px;
  background: #bbb;
  border-radius: 50%;
  cursor: pointer;
}
.dot.active {
  background: #333;
}

/* RESPONSIVE */
@media(max-width: 768px) {
  .slide { flex-direction: column; }
  .slide img { width: 100%; height: 50%; }
  .text { width: 100%; height: 50%; }
  .slider { height: 600px; }
}
</style>
</head>

<body>
<div class="container">

  <h2 class="section-title">Stress And Anxiety</h2>
  <p>Motivating phrases: Living in the present frees us and helps us find well-being. Harming others is a source of anguish and mental suffering. Encourage yourself to treat others well!</p>

  <!-- ====================================================================== -->
  <!-- =========================   STORIES SLIDER   ========================== -->
  <!-- ====================================================================== -->

  <div class="slider" id="slider">

    <!-- Slide 1 -->
    <div class="slide active">
      <img src="https://pymstatic.com/20622/conversions/personas-arrogantes-wide_webp.webp">
      <div class="text">
        <h2>Stories that Inspire</h2>
        <p>Laura was trapped in work-related stress. Exhausted every day, she couldn’t enjoy time with her kids. One day, she tried breathing exercises she found online. Slowly, her stress faded, and she became calmer. Now she plays with her kids and enjoys every moment.</p>
      </div>
    </div>

    <!-- Slide 2 -->
    <div class="slide">
      <img src="https://centrediagonal.com/wp-content/uploads/2023/11/sintomas-estres-y-como-gestionarlo.jpg">
      <div class="text">
        <h2>Stories that Inspire</h2>
        <p>Angela was addicted to video games, restless and rude to his mom. One day, she tried some breathing exercises that she found online. In less than a month, she was calmer, kinder, and more balanced. Gaming no longer controlled her — peace did.</p>
      </div>
    </div>

    <!-- Slide 3 -->
    <div class="slide">
      <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTXGLFVZZ0oNmcA0AmnLp3tDB_JJgnkou8fzA&s">
      <div class="text">
        <h2>Stories that Inspire</h2>
        <p>Javier loved games but became restless and angry with his family. His sister introduced him to breathing exercises. Over time, he grew calmer, kinder, and found balance. Gaming stopped being a problem and became just a hobby.</p>
      </div>
    </div>

    <!-- Slide 4 -->
    <div class="slide">
      <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQTxHnRdsJWW_sIHWzdrORD9L0xDUPZBjwYFg&s">
      <div class="text">
        <h2>Stories that Inspire</h2>
        <p>Emily, a German girl in Colombia, was bullied at her new school. She started doing breathing exercises before class. Soon, she grew calmer and more confident. The bullying stopped, and she was finally accepted for her kindness.</p>
      </div>
    </div>

    <!-- Slide 5 -->
    <div class="slide">
      <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcT2DxE0_MEuUqIYxm5n0k7C5O_rbgDVHGEpRA&s">
      <div class="text">
        <h2>Stories that Inspire</h2>
        <p>Manuel moved to a new city where classmates didn’t accept him. He practiced online breathing exercises, becoming calmer and more confident. Soon, his classmates included him, and he found his place through peace of mind.</p>
      </div>
    </div>

    <!-- Dots -->
    <div class="dots" id="dots"></div>
  </div>

</div>

<!-- ====================================================================== -->
<!-- =========================      SCRIPT      ============================ -->
<!-- ====================================================================== -->
<script>
const slides = document.querySelectorAll('.slide');
const dotsContainer = document.getElementById('dots');
let index = 0;
let interval;

// Crear dots SIN duplicarlos
function createDots() {
  dotsContainer.innerHTML = ""; 
  slides.forEach((_, i) => {
    const dot = document.createElement('div');
    dot.classList.add('dot');
    if (i === 0) dot.classList.add('active');
    dot.addEventListener('click', () => showSlide(i));
    dotsContainer.appendChild(dot);
  });
}
createDots();
const dots = document.querySelectorAll('.dot');

function showSlide(i) {
  slides.forEach((slide, idx) => {
    slide.classList.toggle('active', idx === i);
    dots[idx].classList.toggle('active', idx === i);
  });
  index = i;
  resetInterval();
}

function nextSlide() {
  index = (index + 1) % slides.length;
  showSlide(index);
}

function resetInterval() {
  clearInterval(interval);
  interval = setInterval(nextSlide, 8000);
}
resetInterval();
</script>

</body>
</html>
