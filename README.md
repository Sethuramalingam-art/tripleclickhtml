# tripleclickhtml


var btn = document.getElementById('tripleClk');

btn.addEventListener('click', tripleClick);

let count = 0;
let timer;
function tripleClick() {
		count++;
    if(count===1){
    	timer = setTimeout(()=>{
      count =0;
      }, 1000)
    }
    
    if (count===3) {
    	clearTimeout(timer);
      count =0;
      console.log('tripleclick');
    }

}
