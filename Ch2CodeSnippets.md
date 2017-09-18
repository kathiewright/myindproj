Fan Trick Photography (Chapter 2) Code Snippets


#A1
------------------------------------------------------------------------------------------------

			// global variables
            var photographerCost = 0;  //ref:  page 90
            var totalCost = 0;
            var memoryBook = false;   //ref:  page 98
            var reproductionRights = false;
------------------------------------------------------------------------------------------------

#A2
------------------------------------------------------------------------------------------------

	// sets all form field values to defaults
    function resetForm() {
       document.getElementById("photognum").value = 1;
       document.getElementById("photoghrs").value = 2;
       document.getElementById("membook").checked = memoryBook;
       document.getElementById("reprodrights").checked = reproductionRights;
       document.getElementById("distance").value = 0;
 
    }

------------------------------------------------------------------------------------------------

#B
------------------------------------------------------------------------------------------------
     // resets form when page is reloaded
    window.addEventListener("load", resetForm, false);
------------------------------------------------------------------------------------------------
#C
------------------------------------------------------------------------------------------------

			// global variables
            var photographerCost = 0;  //ref:  page 90
            var totalCost = 0;
            var memoryBook = false;   //ref:  page 98
            var reproductionRights = false;
------------------------------------------------------------------------------------------------

#D
------------------------------------------------------------------------------------------------

      // calculates all costs based on staff and adds to total cost.  Ref:  pp 115-117
    //note that this function is called within the resetForm Function
    function calcStaff() {
       var num = document.getElementById("photognum");     //ref:  pg 115, step 3
       var hrs = document.getElementById("photoghrs");
       var distance = document.getElementById("distance");  //ref pg 130 step 3
       totalCost -= photographerCost;  //uses the compound subtraction assignment operator to subtract the current value of photographerCost
       photographerCost = num.value * 100 * hrs.value + distance.value * num.value;  //multiplies #hrs by 100 (fixed rate) + distance * $1/mile
       totalCost += photographerCost;  //adds the currrent photographer cost back in
       document.getElementById("estimate").innerHTML = "$" + totalCost;  //writes out the amount to the HTML element:  "estimate"
    }
------------------------------------------------------------------------------------------------

#E
------------------------------------------------------------------------------------------------
       calcStaff();   //ref:  pg 116, step 8
       createEventListeners();  //ref pg 117, step 9
------------------------------------------------------------------------------------------------
#F
------------------------------------------------------------------------------------------------
       // creates event listeners
        function createEventListeners() {
           document.getElementById("photognum").addEventListener("change", calcStaff, false);   //ref:  pp 115-117
           document.getElementById("photoghrs").addEventListener("change", calcStaff, false);
           document.getElementById("membook").addEventListener("change", toggleMembook, false);   //ref:  pg 122, step 8
           document.getElementById("reprodrights").addEventListener("change", toggleRights, false);
           document.getElementById("distance").addEventListener("change", calcStaff, false);   //ref:  pg 131, step 4
        }
------------------------------------------------------------------------------------------------
#G
------------------------------------------------------------------------------------------------

			// adds/subtracts cost of memory book from total cost   ref:  pg 120, step 3
      function toggleMembook() {
         (document.getElementById("membook").checked === false) ? totalCost -= 250 : totalCost += 250;
         document.getElementById("estimate").textContent = "$" + totalCost;
      }
      
      // adds/subtracts cost of reproduction rights from total cost   ref pg 121 step 5
    function toggleRights() {
       (document.getElementById("reprodrights").checked === false) ? totalCost -= 1250 : totalCost += 1250;
       document.getElementById("estimate").innerHTML = "$" + totalCost;
    }

------------------------------------------------------------------------------------------------
