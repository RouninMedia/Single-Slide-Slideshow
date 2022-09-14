# Single-Slide-Slideshow
*A Single-Slide Slideshow built with **CSS** and **JS**, in which the same single **HTML** slide repeatedly updates.*

_______
## HTML

```
<div class="circle" data-index="0">red</div>
```
_______
## CSS

```
body {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 260px;
}

.circle {
  width: 180px;
  height: 180px;
  line-height: 180px;
  color: rgb(255, 255, 255);
  font-size: 48px;
  text-align: center;
  background-color: rgb(255, 0, 0);
  border-radius: 50%;
  cursor: pointer;
}

.circle.nextSlide {
  animation: nextSlide 0.9s ease-out;
}

@keyframes nextSlide {
  0%, 100% {opacity: 1; transform: translateX(0);}
  48% {opacity: 1; transform: translateX(-100vw);}
  49% {opacity: 0; transform: translateX(-100vw);}
  50% {opacity: 0; transform: translateX(100vw);}
  51% {opacity: 1; transform: translateX(100vw);}
}
```
_______

## JavaScript

```
const colors = ['red', 'orange', 'yellow', 'green', 'blue', 'indigo', 'violet'];

const circle = document.querySelector('.circle');

const nextSlide = (e) => {
  e.target.classList.add('nextSlide');
  setTimeout(() => e.target.classList.remove('nextSlide'), 910);
  
  setTimeout(() => {
    let index = parseInt(e.target.dataset.index);
    index = (index < (colors.length - 1)) ? (index + 1) : 0;
    e.target.dataset.index = index;
    
    let color = colors[index];
    e.target.textContent = color;
    e.target.style.setProperty('background-color', color); 
  }, 455);
}

circle.addEventListener('click', nextSlide, false);
```
