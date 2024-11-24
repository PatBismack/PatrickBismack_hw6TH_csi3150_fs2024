# HTML Quiz App

## Lesson Outcomes

After implmenting this project, you will have an understanding of:

- JavaScript for DOM manipulation and event handling
- JS Object Literals
- Basic logic for creating quizes

### Prerequisites

- Basic understanding of HTML, CSS, and JavaScript

### Problem Statement

The Quiz App Demo is a web application designed for a timed, multiple-choice questionnaire. The home page features a single button that opens an information card containing general rules and options to either exit or start the quiz.

Once the quiz begins, users have 15 seconds to choose the correct answer from four options related to the displayed question. If a choice is made within the time limit, the timer stops, the correct answer is revealed, and 1 point is awarded for a correct response. If no selection is made before the timer expires, the correct answer is shown, but no points are earned.

After all five questions are answered, a summary screen appears, displaying the total number of correct answers and offering the user the option to replay the quiz or return to the home page.

### Features

- 2-Step confirmation to begin quiz
- View general rules
- Answer multiple-choice questions within 15 seconds
- Highlight correct answers once a option is selected or the time runs out
- See the final score with the option to try again or quit

### Setup

1. Clone the repository to your locale machine
2. Run application in your preferred web browser

#### Run Locally using Live Server

1. Ensure you have the _Live Server extension by Ritwick Dey_ installed
2. Navigate to index.html
3. In the code workspace, right click and select **Open with Live Server**
   ..\* Alternatively, you can use the shortcut **command+L+O** on Mac and **control+L+O** on windows

#### Run using GitHub Pages

1. Ensure you have created a git repository and commit the code to it
2. Navigate to the repository where the code was pushed
3. Click on the settings tab
4. On the left navigation menu, select pages
5. Under the Build and Deploy section and the Branch subsection, set the branch to main and click save
6. After a few minutes, a link will be generated at the top of this page where you can access your deployment

### Directory

`css/
    style.css
index.html
js/
    questions.js
    quizApp.js
index.html
readme.md`

- **index.html** This is the main HTML file that contains the structure for the quiz app including the start button, information card, quiz card and result card.

- **style.css** This is the main cascading style sheet file that contains all the styling for the quiz app including fonts, colors, sizing and transitions. This file is connected to index.html using `<link rel="stylesheet" href="css/style.css">`. The styling is applied to each elemenet using the class attribute.

- **questions.js** This is the main data source that contains all the question related data for the quiz app including question, question number, correct option and all possible options. This file is connected to index.html using `<script src="js/questions.js" defer></script>` but it is not used directly by index.html. This allows for other Javascript files that are connected to index.html to access it.

- **quizApp.js** This is the main JavaScript file that handles the quiz logic including event listeners, timer controls, DOM manipulation and score calculation. This file is connected to index.html using `<script src="js/quizApp.js" defer></script>` and has access to questions.js and style.css through index.html.

### Codebase

#### index.html

This file acts as the main HTML file and is responsible for the structure of the app.

##### Metadata

The head section contains the metadata for the application including language, title, and connections to JS and CSS files.
```<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Quiz App Demo</title>
    <!-- CSS FILE -->
    <link rel="stylesheet" href="css/style.css">
    <!-- This is my personal font awesome kit code. you will have to add your own after you register with email-->
    <script src="https://kit.fontawesome.com/4a4f4b55b0.js" crossorigin="anonymous"></script>

     <!-- Add questions list -->
    <script src="js/questions.js" defer></script>

    <!-- Main logic of the app -->
    <script src="js/quizApp.js" defer></script>
</head>```

#### start_btn

This div contains the start button to begin the quiz.
`<div class="start_btn"><button>Start Quiz</button></div>`

#### info_box

This div contains the card which displays the general rules for the quiz and the button to return to the landing page or begin the quiz. It is made of the sub containers info_title to display the title, info_list to display the rules and buttons to display the two buttons.
`<div class="info_box">

<div class="info-title"><span>Some Rules of this Quiz</span></div>
<div class="info-list">
<div class="info">1. You will have only <span>15 seconds</span> per each question.</div>
<div class="info">2. Once you select your answer, it can't be undone.</div>
<div class="info">3. You can't select any option once time goes off.</div>
<div class="info">4. You can't exit from the Quiz while you're playing.</div>
<div class="info">5. You'll get points on the basis of your correct answers.</div>
</div>
<div class="buttons">
<button class="quit">Exit Quiz</button>
<button class="restart">Continue</button>
</div>

</div>`

#### quiz_box

This div contains the card which display each question that is apart of the quiz. It is made of the subsections title, timer, time_line, que_text, option_list, and footer.
`<div class="quiz_box">

<header>
<div class="title">Demo Quiz App in JavaScript</div>
<div class="timer">
<div class="time_left_txt">Time Left</div>
<div class="timer_sec">15</div>
</div>
<div class="time_line"></div>
</header>
<section>
<div class="que_text">
<!-- Insert questions from ./js/questions.js -->
</div>
<div class="option_list">
<!-- Insert options to questions from ./js/questions.js -->
</div>
</section>

    <!-- footer of Quiz Box -->
    <footer>
        <div class="total_que">
            <!-- insert Question Count Number dynamically from JavaScript App logic -->
        </div>
        <button class="next_btn">Next Que</button>
    </footer>

</div>`

- **title** Contains the name for the quiz
- **timer** Contains a label for the time left and the inital value of the countdown timer
- **time_line** Contains a progress bar to show how much time is left; this is dynamically generated
- **que_text** Contains the question that is beign asked; this is dynamically generated
- **option_list** Contains the options to the question being asked; this is dynamically generated
- **footer** Cotains the question number and the next question button

#### result_box

Thsi div contains the card which displays the final score and option to replay or exit. It contains subsections for an icon, complete_text, score_text, and buttons.
`<div class="result_box">

<div class="icon">
<i class="fas fa-crown"></i>
</div>
<div class="complete_text">You've completed the Quiz!</div>
<div class="score_text">
<!-- insert dynamic user score as Result from JavaScript -->
</div>
<div class="buttons">
<button class="restart">Replay Quiz</button>
<button class="quit">Quit Quiz</button>
</div>

</div>`

- **icon** Contains a logo to display at the end of the quiz
- **complete_text** Contains a message that the user has completed the quiz
- **score_text** Cotains the score the user achieved; this is dynamically generated
- **buttons** Cotains two buttons, one to replay and one to exit and return to the landing page

#### style.css

This file acts as the main stylinh for the quiz app.
`/_ importing google fonts _/
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@200;300;400;500;600;700&display=swap");

- {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Poppins", sans-serif;
  }`

* Reset browser defaults and set the font to Poppins

`body {
background: #a020f0;
}

::selection {
color: #fff;
background: #a020f0;
}

.start_btn,
.info_box,
.quiz_box,
.result_box {
position: absolute;
top: 50%;
left: 50%;
transform: translate(-50%, -50%);
box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
}

.info_box.activeInfo,
.quiz_box.activeQuiz,
.result_box.activeResult {
opacity: 1;
z-index: 5;
pointer-events: auto;
transform: translate(-50%, -50%) scale(1);
}
.start_btn button {
font-size: 25px;
font-weight: 500;
color: #a020f0;
padding: 15px 30px;
outline: none;
border: none;
border-radius: 5px;
background: #fff;
cursor: pointer;
}`

- Set Backgorund color
- Set transition for when the user hovers over a button
- Position cards in the center of the page
- Control visibility of card content
- Style font, color, shape and size of the start button

`.info_box {
width: 540px;
background: #fff;
border-radius: 5px;
transform: translate(-50%, -50%) scale(0.9);
opacity: 0;
pointer-events: none;
transition: all 0.3s ease;
}

.info_box .info-title {
height: 60px;
width: 100%;
border-bottom: 1px solid lightgrey;
display: flex;
align-items: center;
padding: 0 30px;
border-radius: 5px 5px 0 0;
font-size: 20px;
font-weight: 600;
}

.info_box .info-list {
padding: 15px 30px;
}

.info_box .info-list .info {
margin: 5px 0;
font-size: 17px;
}

.info_box .info-list .info span {
font-weight: 600;
color: #a020f0;
}
.info_box .buttons {
height: 60px;
display: flex;
align-items: center;
justify-content: flex-end;
padding: 0 30px;
border-top: 1px solid lightgrey;
}

.info_box .buttons button {
margin: 0 5px;
height: 40px;
width: 100px;
font-size: 16px;
font-weight: 500;
cursor: pointer;
border: none;
outline: none;
border-radius: 5px;
border: 1px solid #a020f0;
transition: all 0.3s ease;
}`

- Defines the shape and size of the info card
- Sets the size, font and positioning of the title
- Sets the font, color and position of the list elements(rules)
- Sets the font, shape, size and color of two buttons

`.quiz_box {
width: 550px;
background: #fff;
border-radius: 5px;
transform: translate(-50%, -50%) scale(0.9);
opacity: 0;
pointer-events: none;
transition: all 0.3s ease;
}

.quiz_box header {
position: relative;
z-index: 2;
height: 70px;
padding: 0 30px;
background: #fff;
border-radius: 5px 5px 0 0;
display: flex;
align-items: center;
justify-content: space-between;
box-shadow: 0px 3px 5px 1px rgba(0, 0, 0, 0.1);
}

.quiz_box header .title {
font-size: 20px;
font-weight: 600;
}

.quiz_box header .timer {
color: #682a8f;
background: #cce5ff;
border: 1px solid #b8daff;
height: 45px;
padding: 0 8px;
border-radius: 5px;
display: flex;
align-items: center;
justify-content: space-between;
width: 145px;
}

.quiz_box header .timer .time_left_txt {
font-weight: 400;
font-size: 17px;
user-select: none;
}

.quiz_box header .timer .timer_sec {
font-size: 18px;
font-weight: 500;
height: 30px;
width: 45px;
color: #fff;
border-radius: 5px;
line-height: 30px;
text-align: center;
background: #343a40;
border: 1px solid #343a40;
user-select: none;
}

.quiz_box header .time_line {
position: absolute;
bottom: 0px;
left: 0px;
height: 3px;
background: #a020f0;
}`

- Defines the shape and size of the quiz card
- Sets the size, font and positioning of the title
- Sets the color, size and position of the timer

`section {
padding: 25px 30px 20px 30px;
background: #fff;
}

section .que_text {
font-size: 25px;
font-weight: 600;
}

section .option_list {
padding: 20px 0px;
display: block;
}

section .option_list .option {
background: aliceblue;
border: 1px solid #84c5fe;
border-radius: 5px;
padding: 8px 15px;
font-size: 17px;
margin-bottom: 15px;
cursor: pointer;
transition: all 0.3s ease;
display: flex;
align-items: center;
justify-content: space-between;
}

section .option_list .option:last-child {
margin-bottom: 0px;
}

section .option_list .option:hover {
color: #601391;
background: #cce5ff;
border: 1px solid #b8daff;
}

section .option_list .option.correct {
color: #155724;
background: #d4edda;
border: 1px solid #c3e6cb;
}

section .option_list .option.incorrect {
color: #721c24;
background: #f8d7da;
border: 1px solid #f5c6cb;
}

section .option_list .option.disabled {
pointer-events: none;
}

section .option_list .option .icon {
height: 26px;
width: 26px;
border: 2px solid transparent;
border-radius: 50%;
text-align: center;
font-size: 13px;
pointer-events: none;
transition: all 0.3s ease;
line-height: 24px;
}
.option_list .option .icon.tick {
color: #23903c;
border-color: #23903c;
background: #d4edda;
}

.option_list .option .icon.cross {
color: #a42834;
background: #f8d7da;
border-color: #a42834;
}`

- Defines the style for the dynamic content on the quiz card
- Sets the size, font and positioning of the question
- Sets the color, size and position of the list of choices
- Defines the transitions correct/incorrect when an option is selected
- Disables the ablilty to select an option after one is clicked or timer runs out
- Sets the size, color, shaoe and transition for check/x logo

`footer {
height: 60px;
padding: 0 30px;
display: flex;
align-items: center;
justify-content: space-between;
border-top: 1px solid lightgrey;
}

footer .total_que span {
display: flex;
user-select: none;
}

footer .total_que span p {
font-weight: 500;
padding: 0 5px;
}

footer .total_que span p:first-child {
padding-left: 0px;
}

footer button {
height: 40px;
padding: 0 13px;
font-size: 18px;
font-weight: 400;
cursor: pointer;
border: none;
outline: none;
color: #fff;
border-radius: 5px;
background: #a020f0;
border: 1px solid #a020f0;
line-height: 10px;
opacity: 0;
pointer-events: none;
transform: scale(0.95);
transition: all 0.3s ease;
}

footer button:hover {
background: #7803c0;
}

footer button.show {
opacity: 1;
pointer-events: auto;
transform: scale(1);
}`

- Defines the style for the footer on the quiz card
- Sets the size, font and positioning of the number of question completed
- Sets the color, size and position of the continue button
- Defines the transitions to display the continue button once the question has been answered

`.result_box {
background: #fff;
border-radius: 5px;
display: flex;
padding: 25px 30px;
width: 450px;
align-items: center;
flex-direction: column;
justify-content: center;
transform: translate(-50%, -50%) scale(0.9);
opacity: 0;
pointer-events: none;
transition: all 0.3s ease;
}

.result_box .icon {
font-size: 100px;
color: #a020f0;
margin-bottom: 10px;
}

.result_box .complete_text {
font-size: 20px;
font-weight: 500;
}

.result_box .score_text span {
display: flex;
margin: 10px 0;
font-size: 18px;
font-weight: 500;
}

.result_box .score_text span p {
padding: 0 4px;
font-weight: 600;
}

.result_box .buttons {
display: flex;
margin: 20px 0;
}

.result_box .buttons button {
margin: 0 10px;
height: 45px;
padding: 0 20px;
font-size: 18px;
font-weight: 500;
cursor: pointer;
border: none;
outline: none;
border-radius: 5px;
border: 1px solid #a020f0;
transition: all 0.3s ease;
}

.buttons button.restart {
color: #fff;
background: #a020f0;
}

.buttons button.restart:hover {
background: #8304d1;
}

.buttons button.quit {
color: #a020f0;
background: #fff;
}

.buttons button.quit:hover {
color: #fff;
background: #8604d6;
}`

- Defines the size, shape, and position for the results card
- Sets the size and positioning of the crown icon
- Sets the size and positionign of the score texr
- Sets the color, size, transitions and position of the replay and quit button

#### questions.js

This file acts as the main source of data for the quiz app. It is made of an array made up of JavaScript object literals.
_Object Literal Format_
`{
    numb: 1,
    question: "Question",
    answer: "Answer",
    options: [
      "Answer",
      "Alternative 1",
      "Alternative 2",
      "Alternative 3",
    ],
  }`

- numb: takes numbers of type integer
  ..\* Note that the numb field should follow numerically order
- question: takes the question that is being asked as a strting
- answer: takes the answer to the question that is being asked as a string
- options: takes an array of 4 strings made up of the answer string provided previously and 3 alternative answers
  --\*Note that where the answer is placed inside the options array will determine where it is displayed. It is best to put answer in a different index each time

#### QuizApp.js

`// if startQuiz button clicked
start_btn.addEventListener("click", (e) => {
info_box.classList.add("activeInfo"); //show info box
});

// if exitQuiz button clicked
exit_btn.addEventListener("click", (e) => {
info_box.classList.remove("activeInfo"); //hide info box
});

// if continueQuiz button clicked
continue_btn.addEventListener("click", (e) => {
info_box.classList.remove("activeInfo"); //hide info box
quiz_box.classList.add("activeQuiz"); //show quiz box
showQuetions(0); //calling showQestions function
queCounter(1); //passing 1 parameter to queCounter
startTimer(15); //calling startTimer function
startTimerLine(0); //calling startTimerLine function
});

// Variables to control quiz operations
let timeValue = 15;
let que_count = 0;
let que_numb = 1;
let userScore = 0;
let counter;
let counterLine;
let widthValue = 0;

// if restartQuiz button clicked
restart_quiz.addEventListener("click", (e) => {
quiz_box.classList.add("activeQuiz"); //show quiz box
result_box.classList.remove("activeResult"); //hide result box
timeValue = 15;
que_count = 0;
que_numb = 1;
userScore = 0;
widthValue = 0;
showQuetions(que_count); //calling showQestions function
queCounter(que_numb); //passing que_numb value to queCounter
clearInterval(counter); //clear counter
clearInterval(counterLine); //clear counterLine
startTimer(timeValue); //calling startTimer function
startTimerLine(widthValue); //calling startTimerLine function
timeText.textContent = "Time Left"; //change the text of timeText to Time Left
next_btn.classList.remove("show"); //hide the next button
});

// if quitQuiz button clicked
quit_quiz.addEventListener("click", (e) => {
window.location.reload(); //reload the current window
});

// if Next Question button is clicked
next_btn.addEventListener("click", (e) => {
//check if it does not exceed max questions
if (que_count < questions.length - 1) {
que_count++; //increment the que_count value
que_numb++; //increment the que_numb value
showQuetions(que_count); //calling showQestions function
queCounter(que_numb); //passing que_numb value to queCounter
clearInterval(counter); //clear counter
clearInterval(counterLine); //clear counterLine
startTimer(timeValue); //calling startTimer function
startTimerLine(widthValue); //calling startTimerLine function
timeText.textContent = "Time Left"; //change the timeText to Time Left
next_btn.classList.remove("show"); //hide the next button
} else {
clearInterval(counter); //clear counter
clearInterval(counterLine); //clear counterLine
showResult(); //calling showResult function
}
});`

##### Event Listener

- Start Quiz Button: Adds an event listener to the start button to show the info card when clicked
- Exit Quiz Button: Adds an event listener to the exit button to hide the info card when clicked
- Continue Quiz Button: Adds an event listener to the continue button to hide the info card, show the quiz card, and initialize the quiz by calling functions to display questions, start the timer, and update the question counter
- Restart Quiz Button: Adds an event listener to the restart button to reset the quiz state and start the quiz again
- Quit Quiz Button: Adds an event listener to the quit button to return to the home screen
- Next Question Button: Adds an event listener to the next button to proceed to the next question, update the question counter, and reset the timer

##### Functions

`// getting questions and options from array
// If you have lesser or more number of options you need to change this code
function showQuetions(index) {
const que_text = document.querySelector(".que_text");

//creating a new span and div tag for question and option and passing the value using array index
// self exercise: re-write the following using backtick syntax for string in JS instead of concatenation operator
let que_tag =
"<span>" +
questions[index].numb +
". " +
questions[index].question +
"</span>";
let option_tag =
'<div class="option"><span>' +
questions[index].options[0] +
"</span></div>" +
'<div class="option"><span>' +
questions[index].options[1] +
"</span></div>" +
'<div class="option"><span>' +
questions[index].options[2] +
"</span></div>" +
'<div class="option"><span>' +
questions[index].options[3] +
"</span></div>";
que_text.innerHTML = que_tag; //adding new (child) span tag inside que_tag
option_list.innerHTML = option_tag; //adding new (child) div tag inside option_tag

const option = option_list.querySelectorAll(".option");

// set onclick attribute to all available options
for (i = 0; i < option.length; i++) {
option[i].setAttribute("onclick", "optionSelected(this)");
}
}`

This function takes the index of the question to generate the content for the quiz card

- Dynamically generates the container that holds the question and its number
- Dynamically generates the cotainer that holds the 4 options
- Sets their onClick attribute for each option

`// create new div tags for right or wrong tick icons
let tickIconTag = '<div class="icon tick"><i class="fas fa-check"></i></div>';
let crossIconTag = '<div class="icon cross"><i class="fas fa-times"></i></div>';

//if user clicked on option
function optionSelected(answer) {
clearInterval(counter); //clear counter
clearInterval(counterLine); //clear counterLine
let userAns = answer.textContent; //getting user selected option
let correcAns = questions[que_count].answer; //getting correct answer from array
const allOptions = option_list.children.length; //getting all option items

//if user selected option is equal to array's correct answer
if (userAns == correcAns) {
userScore += 1; //update total score value increment by 1
answer.classList.add("correct"); //add green color to correct selected option
answer.insertAdjacentHTML("beforeend", tickIconTag); //add tick icon to correct selected option
console.log("Correct Answer");
console.log("Your correct answers = " + userScore);
} else {
answer.classList.add("incorrect"); //add red color to correct selected option
answer.insertAdjacentHTML("beforeend", crossIconTag); //add cross icon to correct selected option
console.log("Wrong Answer");

    for (i = 0; i < allOptions; i++) {
      if (option_list.children[i].textContent == correcAns) {
        //if there is an option which is matched to an array answer
        option_list.children[i].setAttribute("class", "option correct"); //add green color to matched option
        option_list.children[i].insertAdjacentHTML("beforeend", tickIconTag); //add tick icon to matched option
        console.log("Auto selected correct answer.");
      }
    }

}
for (i = 0; i < allOptions; i++) {
option_list.children[i].classList.add("disabled"); //once user select an option, disable all options
}
next_btn.classList.add("show"); //show the next button if user selected any option
}`

This function is responsible for handling when a user selects and option

- Resets the value for counter and counterLine (timer)
- Fetches the text related to selected option and assigns it to userAns
- Fetches the correct answer for the question and assigns it to correcAns
- Comapre userAns and CorrecAns
  .._ If the two variables match, userScore is increased by 1, the selected option is styled using the correct class, and displays the tick icon
  .._ If the two variables don't match, userScore is not increased, the selected option is styled using the incorrect class and displays the cross icon
- Disables all options from being selected
- Displays the next button

`// display for result box based on user performance
function showResult() {
  info_box.classList.remove("activeInfo"); //hide info box
  quiz_box.classList.remove("activeQuiz"); //hide quiz box
  result_box.classList.add("activeResult"); //show result box
  const scoreText = result_box.querySelector(".score_text");
  if (userScore > 3) {
    // if user scored more than 3
    //create a new span tag and pass the user score number and total question number
    let scoreTag =
      "<span>and congrats! , You got <p>" +
      userScore +
      "</p> out of <p>" +
      questions.length +
      "</p></span>";
    scoreText.innerHTML = scoreTag; //add new span tag inside score_Text
  } else if (userScore > 1) {
    // if user scored more than 1
    let scoreTag =
      "<span>and nice , You got <p>" +
      userScore +
      "</p> out of <p>" +
      questions.length +
      "</p></span>";
    scoreText.innerHTML = scoreTag;
  } else {
    // if user scored less than 1
    let scoreTag =
      "<span>and sorry , You got only <p>" +
      userScore +
      "</p> out of <p>" +
      questions.length +
      "</p></span>";
    scoreText.innerHTML = scoreTag;
  }
}`

- Hide the info and quiz card
- Get the user score and determines the rank
  .._ If the userScore > 3, displays congrats with score
  .._ If the userScore > 1, displays nice with score
  ..\* If the userScore = 0, displays sorry with score
- Display the user score

`// control the timer and actions associated to it
function startTimer(time) {
  counter = setInterval(timer, 1000);
  function timer() {
    timeCount.textContent = time; //change the value of timeCount with time value
    time--; //decrement the time value
    if (time < 9) {
      //if timer is less than 9
      let addZero = timeCount.textContent;
      timeCount.textContent = "0" + addZero; //add a 0 before time value
    }
    if (time < 0) {
      //if timer is less than 0
      clearInterval(counter); //clear counter
      timeText.textContent = "Time Off"; //change the time text to time off
      const allOptions = option_list.children.length; //get all option items
      let correcAns = questions[que_count].answer; //get correct answer from array
      for (i = 0; i < allOptions; i++) {
        if (option_list.children[i].textContent == correcAns) {
          //if there is an option which is matched to an array answer
          option_list.children[i].setAttribute("class", "option correct"); //add green color to matched option
          option_list.children[i].insertAdjacentHTML("beforeend", tickIconTag); //add tick icon to matched option
          console.log("Time Off: Auto selected correct answer.");
        }
      }
      for (i = 0; i < allOptions; i++) {
        option_list.children[i].classList.add("disabled"); //once user select an option then disabled all options
      }
      next_btn.classList.add("show"); //show the next button if user selected any option
    }
  }
}`

- Start the timer and set it's interval to 1 second per tick
- Update the timer display. If the time < 9 seconds add leading 0s
- When the timer runs out
  .._ Stop the timer using clearInterval
  .._ Change text to Time Off
  .._ Highlight correct answer
  .._ Disable all options from eing selected
  ..\* Display the next question button

`// Shows a progress bar mirroring timer value left
function startTimerLine(time) {
  counterLine = setInterval(timer, 29);
  function timer() {
    time += 1; //upgrading time value with 1
    time_line.style.width = time + "px"; //increasing width of time_line with px by time value
    if (time > 549) {
      //if time value is greater than 549
      clearInterval(counterLine); //clear counterLine
    }
  }
}`

- Start progress bar with an interval of 29 milliseconds
- Update progress bar based on each tick
- Stop progress bar when time value exceeds 549 milliseconds

`function queCounter(index) {
  //creating a new span tag and passing the question number and total question
  let totalQueCounTag =
    "<span><p>" +
    index +
    "</p> of <p>" +
    questions.length +
    "</p> Questions</span>";
  bottom_ques_counter.innerHTML = totalQueCounTag; //adding new span tag inside bottom_ques_counter
}`

- Create current question number text and total number of questions
- Update counter display
