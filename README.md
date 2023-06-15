# TableScrollingWithDots
Help you to scroll table form left to right by clicking on dot below as pagination.
<p> Code to make table scrollable on click of dot using javascript. Create a table and dots div and add <code>scrollTableWrapper(0)</code> function to each dot with dot no passed as parameter </p>
<code>
  <script>
        let currentSettWidth = 0;
        let currentDot = 1;
        const container =  document.querySelector(".wrapper");
        const table = document.querySelector(".table");
        const allDots =document.querySelectorAll(".dot");
        const totalNOodDots = parseInt(allDots.length);
        let widthtocalulatRightScrollPositin = 0;
        let widthToAppltArray = [];
        const tableWidth = table.scrollWidth;
        const tableWidthToScroll = tableWidth/totalNOodDots;
        const maxScroll = table.scrollWidth - container.offsetWidth;
        let countofdots = 0;
        allDots.forEach((element) => {
            if(countofdots > 0){
                widthtocalulatRightScrollPositin = widthtocalulatRightScrollPositin + tableWidthToScroll;
            }
            if(countofdots == (totalNOodDots - 1)){
                widthtocalulatRightScrollPositin = maxScroll;
            }
            widthToAppltArray.push(widthtocalulatRightScrollPositin);
            countofdots++;
        })
        const scrollTableWrapper = (dotNo) => {
            var currentScroll = container.scrollLeft;
            if (currentScroll >= Math.floor(widthToAppltArray[dotNo+1])) {
                currentScroll = 0;
            }
            // Calculate the new scroll position
            var newScroll = widthToAppltArray[dotNo];
            // Limit the scroll position to the maximum value
            if (newScroll > maxScroll) {
                newScroll = maxScroll;
            }
            // Set the new scroll position
            container.scrollLeft = newScroll;
        }
    </script>
  </code>
