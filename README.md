<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Calculator</title.
</head>
      <style>
        *{
    padding: 0;
    margin: 0;
    box-sizing: border-box;
    outline: 0;
    transition: all 0.5s ease;
}

body{
    font-family: sans-serif;
    background-image: linear-gradient(to bottom right, rgba(79, 51, 176, 1), rgba(210, 53, 165));
}

a{
    text-decoration: none;
    color: #fff;
}

.container{
    height: 100vh;
    width: 100vw;
    display: grid;
    place-items: center;
}

.calculator{
    position: relative;
    height: auto;
    width: auto;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 0 30px #000;
}

.theme-toggler{
    position: absolute;
    top: 30px;
    right: 30px;
    color: #fff;
    cursor: pointer;
    z-index: 1;
}

.theme-toggler.active{
    color: #333;
}

.theme-toggler.active::before{
    background-color: #fff;
}

.theme-toggler::before{
    content: "";
    height: 30px;
    width: 30px;
    position: absolute;
    top: 50%;
    transform: translate(-50%, -50%);
    border-radius: 50%;
    background-color: #333;
    z-index: -1;
}

#display{
    margin: 0 10px;
    height: 150px;
    width: auto;
    max-width: 270px;
    display: flex;
    align-items: flex-end;
    justify-content: flex-end;
    font-size: 30px;
    margin-bottom: 20px;
    overflow-x: scroll;
}

#display::-webkit-scrollbar{
    display: block;
    height: 3px;
}

button{
    height: 60px;
    width: 60px;
    border: 0;
    border-radius: 30px;
    margin: 5px;
    font-size: 20px;
    cursor: pointer;
    transition: all 200ms ease;
}

button:hover{
    transform: scale(1.1);
}

/* Light Theme */
.calculator{
    background-color: #fff;
}

#display{
    color: #0a1e23;
}

#clear{
    background-color: #ffd5d8;
    color: #fc4552;
}

.btn-number, .btn-operator{
    background-color: #c3eaff;
    color: #000;
}

.btn-equal{
    background-color: #adf9e7;
    color: #000;
}

/* Dark Theme */
.calculator.dark{
    background-color: #071115;
}

.calculator.dark #display{
    color: #f8fafd;
}

#clear{
    background-color: #2d191e;
    color: #bd3740;
}

.calculator.dark button.btn-number, .btn-operator{
    background-color: #2e1f39;
    color: #f8fafb;
}

.calculator.dark button.btn-equal{
    background-color: #223323;
    color: #ffffff;
}
      </style>
<body>
    <!-- Dark/Light Theme -->
    <div class="container">
        <div class="calculator dark">
            <div class="theme-toggler active">
                <i class="toggler-icon"></i>
            </div>
            <div class="display-screen">
                <div id="display"></div>
            </div>
    <!-- Calculator Buttons -->
            <div class="buttons">
                <table>
                    <tr>
                        <td><button class="btn-operator" id="clear">C</button></td>
                        <td><button class="btn-operator" id="clear">CE</button></td>
                        <td><button class="btn-operator" id="*">&times;</button></td>
                        <td><button class="btn-operator" id="backspace"><</button></td>
                    </tr>
                    <tr>
                        <td><button class="btn-number" id="7">7</button></td>
                        <td><button class="btn-number" id="8">8</button></td>
                        <td><button class="btn-number" id="9">9</button></td>
                        <td><button class="btn-operator" id="/">&divide;</button></td>
                    </tr>
                    <tr>
                        <td><button class="btn-number" id="4">4</button></td>
                        <td><button class="btn-number" id="5">5</button></td>
                        <td><button class="btn-number" id="6">6</button></td>
                        <td><button class="btn-operator" id="+">+</button></td>
                    </tr>
                    <tr>
                        <td><button class="btn-number" id="1">1</button></td>
                        <td><button class="btn-number" id="2">2</button></td>
                        <td><button class="btn-number" id="3">3</button></td>
                        <td><button class="btn-operator" id="-">-</button></td>
                    </tr>
                    <tr>
                        <td><button class="btn-operator" id="(">(</button></td>
                        <td><button class="btn-number" id="0">0</button></td>
                        <td><button class="btn-operator" id=")">)</button></td>
                        <td><button class="btn-equal" id="equal">=</button></td>
                    </tr>
                </table>
            </div>
        </div>
      </div>
    <script>
      // Calculation Section
const display = document.querySelector("#display");
const buttons = document.querySelectorAll("button");

buttons.forEach((item) => {
    item.onclick = () => {
        if (item.id == "clear") {
            display.innerText = "";
        }
        else if (item.id == "backspace") {
            let string = display.innerText.toString();
            display.innerText = string.substr(0, string.length - 1);
        }
        else if (display.innerText != "" && item.id == "equal") {
            display.innerText = eval(display.innerText);
        }
        else if (display.innerText == "" && item.id == "equal") {
            display.innerText = "";
        }
        else {
            display.innerText += item.id;
        }
    }
})

// Light/Dark Theme
const themeToggleBtn = document.querySelector(".theme-toggler");
const calculator = document.querySelector(".calculator");
const toggleIcon = document.querySelector(".toggler-icon");
let isDark = true;
themeToggleBtn.onclick = () => {
    calculator.classList.toggle("dark");
    themeToggleBtn.classList.toggle("active");
    isDark = !isDark;
}
    </script>
</body>
</html>
