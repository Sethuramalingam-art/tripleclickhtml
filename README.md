# tripleclickhtml

let count = 0;
let elements = new Map();

document.addEventListener('click', function (event) {
  let countdown;
  
  function reset () {
    count = 0;
    countdown = null;
  }
  
  count++;
  
  if (count === 3) {
    if (!elements.has(event.target)) {
      elements.set(event.target, 1);
    } else {
      let currentCount = elements.get(event.target);
      currentCount++;
      elements.set(event.target, currentCount);
    }
    
    let tripleClick = new CustomEvent('trplclick', {
      bubbles: true,
      detail: {
        numberOfTripleClicks: elements.get(event.target)
      }
    });
    
    event.target.dispatchEvent(tripleClick);
    reset();
  }
  
  if (!countdown) {
    countdown = window.setTimeout(function () {
      reset();
    }, 500);
  }
});

document.addEventListener('trplclick', function (event) {
  console.log('This element has been triple clicked', event.detail.numberOfTripleClicks, 'times');
});
