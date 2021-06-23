<!--根據ID顯示所有商品-->
<template >

  <div class="container">
    <span >
      helloWorld <!--測試顯示用-->
      <br>

      <div class="dropdown" @click="toggleDropMenu"  style="display:inline;">
        <div class="dropdown-trigger" style="display:inline;">
          <button class="button" aria-haspopup="true" aria-controls="dropdown-menu">
            <span id="DropDownMenuDisplay" >查詢物品</span>
            <span class="icon is-small">
              <i class="fa fa-angle-down" aria-hidden="true"></i>
            </span>
          </button>
        </div>
        <div class="dropdown-menu" id="dropdown-menu" role="menu" >
          <div class="dropdown-content">
            <a  class="dropdown-item" @click="toggleMenuSelection('DMselect1')" id="DMselect1">
              查詢物品
            </a>
            <a  class="dropdown-item" @click="toggleMenuSelection('DMselect2')" id="DMselect2">
              所有項目
            </a>
            <a class="dropdown-item" @click="toggleMenuSelection('DMselect3')" id="DMselect3">
              活動名稱
            </a>
          </div>
        </div>
      </div>
      &nbsp;&nbsp;
      <input class="box" type="search" style="display:inline; height: 20px" id="serchBox">
      &nbsp;
      <button class="button" @click="MenuSearch">送出</button>


    </span>
    <>
    <div class="content container is-fluid" id="displayResult" style="width: 240px">
      <!-- Here will display result -->
    </div>
  </div>
</template>

<script>
//import MenuItem from "@/components/MenuItem";
import productMenu from "../../menu-list-data.json" //將JSON 資料拉出 放到productMenu 裡


export default {
  name: "menu",
  computed:{
    // ItemMenu,
  },
  components:
      {
      }
  ,
  data()
  {
    return{
      productMenu
    } //將資料提供給TEMPLATE 使用
  },
  methods:
  {
      toggleDropMenu()
      {
        var dropdown = document.querySelector('.dropdown');
        dropdown.classList.toggle('is-active');
      },
      toggleMenuSelection(thisID)
      {
        var display = document.getElementById("DropDownMenuDisplay");
        var select = document.getElementById(thisID);
        display.innerText = select.innerText;
      },
      display(productResult)
      {
        var displayText = "<ul>";
        var display = document.getElementById("displayResult");
        for(let i in productResult)
        {
          displayText += "<li>" + productResult[i].title + "</li>";
        }
        displayText+="</ul>";
        display.innerHTML = displayText;
      },
      MenuSearch()
      {
        var displayProduct = [];
        let index = 0;
        var searchBox = document.getElementById("serchBox").value;
        for(var productIndex = 0; productIndex < Object.keys(productMenu).length;productIndex++) {
          if(productMenu[productIndex].title.match(searchBox) != null && searchBox != "")
            displayProduct[index++] = productMenu[productIndex];
        }
        for(let i in displayProduct)
        {
          console.log(displayProduct[i].title);
        }
        this.display(displayProduct);
      }

  }
}


</script>

<style scoped>
@import "https://cdn.staticfile.org/font-awesome/4.7.0/css/font-awesome.css";
</style>