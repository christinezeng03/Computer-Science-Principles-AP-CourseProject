My program was written using JavaScript. The purpose of the program is to teach the user how to properly take care of a bean plant over the course of 8 weeks by providing the right amounts of water, nutrients, and environment. My program consists of three main interactive actions, the first being the planting stage where the user must click on the bean seed to plant it into the soil, second the user should fertilize their plant once every four weeks adding an additional 1 mm to the height of the plant, and finally the user should water their plant a medium amount of water, the best results will appear when the user waters near 50 mL every week. The height of the bean plant displayed on the end Screen will reflect how well the user has taken care of their plant, better care equals greater height. 

I independently worked on each element and their corresponding code and UI individually, solving difficulties along the way, and only continuing onto the next when I finished. One difficulty that I encountered while writing the algorithms was how to restrict the user’s fertilizer amount. My first function couldn’t correctly determine the value of wellFertilized when the user applied more fertilizer than what was necessary. I resolved the problem by adding a new variable for the fertilizer amount. 100g is added to the variable when the user fertilizes and 25g is subtracted for each incrementing week. Only when the amount is less than/equal to 100g and greater than 0g could the user receive the extra fertilizer height. Another difficulty I encountered was determining the best amount of water to water the plant every week that would generate the greatest height. I originally choose 40 mL/week as it was an option to choose on the screen, but when I let my friend test my program, it became too easy for her, so I changed the ideal watering amount to be near 50mL/week(not a choice on the screen) to make the program more difficult and realistic. 

Code Segment 
//Main Algorithm 
//finds and displays the total height of the plant after water and fertilizer function findHeight() { findWaterAmount(); findFertilize(); 
if (wellFertilized) { 
height = height+1; 
setProperty("score", "text", height+" mm"); } 
else { 
height = height+0; 
setProperty("score", "text", height+" mm"); } 
} //Child Algorithm 1 //finds the height of the plant based off average amount of water watered function findWaterAmount() { 
averageWater = totalWater/week; 
if (averageWater<60&&averageWater>=40) { 
    height = height+5; 
    } 
else if ((averageWater<40&&averageWater>=20)||(averageWater>=60&&averageWater<80)) { 
    height = height+2; 
    } 
else if ((averageWater<20&&averageWater>=10)||(averageWater>=80&&averageWater<90)) { 
    height = height+1; 
    } 
else { 
    height = height+0.5; 
    } 
} //Child Algorithm 2 and my Abstraction //finds if the wellFertilized variable is true or false(if the plant is well Fertilized) 

function findFertilize() { 
    if (fertilizerAmount<=100&&fertilizerAmount>0) {    
        wellFertilized = true; 
        } 
    else { 
        wellFertilized = false; } 
    } 
    //when the user clicks the nextWeek button it 
    //finds and displays the week & decreases the fertilizer amount by 25g every week function nextWeek() { 
    if (week<8) { 
        week = week+1; 
        fertilizerAmount = fertilizerAmount-25; 
        if (fertilizerAmount<0) { 
            fertilizerAmount = 0; 
        } 
        setProperty("week", "text", week); 
        hideElement("endButton"); 
    } 
    else if ((week==8)) { 
        showElement("endButton"); 
        } 
    } 

//adds 100g to fertilizerAmount when fertilizer image is clicked //displays the number of times the fertilzer image was clicked function fertilizerText() { 
    fertilizer = fertilizer+1; 
    fertilizerAmount = fertilizerAmount+100; 
    setProperty("fertilizerNumber", "text", fertilizer+" times"); 
} 

Written Response 

The main algorithm findHeight combines the information gathered from its two child functions: findWaterAmount and findFertilize, calculating the total height of the bean plant with if-then statements. The first function findWaterAmount calculates the average amount of water per week, dividing the total amount of water the user has selected so far by the number of weeks the game has lasted, and uses an if-else-if statement to produce the height from the average amount of water(near 50mL produces best height). The other child function findFertilize computes the variable wellFertilized by checking if the fertilizer image is clicked once every four weeks. The variable is set to true if the variable fertilizerAmount is within 1 and 100; otherwise the variable is set to false. The variable fertilizerAmount represents the remaining amount of fertilizer to the plant, adding 100g to when the user fertilized and subtracting 25g for each incrementing week. In findHeight, if wellFertilized is true then the height from the watering will increase by one, if wellFertilized is false then the height from the watering will not increase. The resulting height is the total height of the plant over 8 weeks, which educates the user on how to grow plants effectively.



Code Segment 
//Child Algorithm 2 and my Abstraction 
//finds if the wellFertilized variable is true or false(if the plant is well Fertilized) 

function findFertilize() { 
    if (fertilizerAmount<=100&&fertilizerAmount>0) { 
        wellFertilized = true; 
        } 
    else { 
        wellFertilized = false; 
    } 
} 


Written Response 
The function findFertilize is an abstraction that I wrote myself. It calculates if the plant is well fertilized; if the fertilizerAmount is less than or equal to 100g and greater than 0g then the wellFertilized boolean variable is true, if the fertilizer amount isn’t then the wellFertilized boolean variable is false. findFertilize is called in my main algorithm findHeight contributing to the calculation of the total plant height. It also runs the display on the screen that indicates if the user fertilized their plant. This abstraction manages complexity because findFertilize is called in my program twice, if I did not write the function findFertilize, the same five lines of code would appear twice in my program causing confusion and redundancy. With findFertilize I am able to simplify this behavior that appears in my program multiple times into one function/line of code, achieving generalization and simplicity. 
