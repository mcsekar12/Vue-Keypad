<template>
<div>

<table id="phone">
    <tr>
        <td colspan="3">
            <input type="text" id="result" v-model="displayValue"/>
        </td>
    </tr>
    <tr>
        <td data-value="1" class="key"  >
            <button data-value="1" @mousedown="onKeypadPress" @mouseup="clearPress">1
                <span>. , !</span>
            </button>
        </td>
        <td>
            <button data-value="2" class="key"  @mousedown="onKeypadPress" @mouseup="clearPress">2
                <span>a b c</span>
            </button>
        </td>
        <td>
            <button data-value="3" class="key"  @mousedown="onKeypadPress" @mouseup="clearPress">3
                <span>d e f</span>
            </button>
        </td>
    </tr>
    <tr>
        <td>
            <button data-value="4" class="key" @mousedown="onKeypadPress" @mouseup="clearPress">4
                <span>g h i</span>
            </button>
        </td>
        <td>
            <button data-value="5" class="key" @mousedown="onKeypadPress" @mouseup="clearPress">5
                <span>j k l</span>
            </button>
        </td>
        <td>
            <button data-value="6" class="key" @mousedown="onKeypadPress" @mouseup="clearPress">6
                <span>m n o</span>
            </button>
        </td>
    </tr>
    <tr>
        <td><button data-value="7" class="key" @mousedown="onKeypadPress" @mouseup="clearPress">7
            <span>p q r s</span>
            </button>
        </td>
        <td>
            <button data-value="8" class="key" @mousedown="onKeypadPress" @mouseup="clearPress">8
                <span>t u v</span>
            </button>
        </td>
        <td>
            <button data-value="9" class="key" @mousedown="onKeypadPress" @mouseup="clearPress">9
                <span>w x y z</span>
            </button>
        </td>
    </tr>
    <tr>
        <td><button data-value="*" class="key" @mousedown="onKeypadPress" @mouseup="clearPress">*</button></td>
        <td><button data-value="0" class="key" @mousedown="onKeypadPress" @mouseup="clearPress">0</button></td>
        <td><button data-value="#" class="key" @mousedown="onKeypadPress" @mouseup="clearPress" >#</button></td>
    </tr>
</table>
</div>
</template>

<script>
export default {
  name: 'app',
 data(){
   return {
    displayValue:'',
    cycle:null,
    items:{
    "1":['1','.',',','!'],
    "2":['2','a','b','c'],
     "3":['3','d','e','f'],
    "4":['4','g','h','i'],
     "5":['5','j','k','l'],
    "6":['6','m','n','o'],
    "7":['7','p','q','r','s'],
     "8":['8','t','u','v'],
    "9":['9','w','x','y','z'],
    "*":['*'],
     "0":['0'],
    "#":['#']
    }
   }
  },
  methods:{
  onKeypadPress(event){
  let val=event.target.dataset.value;
  let i=0;
  let item=this.items[val];
  let itemsLen=item.length;
  this.displayValue=this.displayValue+item[0];
  i++;
  
  this.cycle=setInterval(()=>{
  this.displayValue=this.displayValue.slice(0, -1) +item[i];
  i++;
  if(i>=itemsLen){
  i=0;
  }
  },1000)
    
  },
  clearPress(){
clearInterval(this.cycle);
  }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#phone button {
  height: 50px;
  width: 75px;
}
#phone button span {
  display: block;
  margin-top: 5px;
  font-size: 10px;
}
#result {
  width: 225px;
  height: 25px;
  margin-left: 2px;
}
button span {
  pointer-events: none;
}
</style>
