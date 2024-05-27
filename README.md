<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Text Box Chain</title>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Roboto+Condensed:wght@800&display=swap">
<style>
  .container {
    position: absolute; /* Position the container */
    left: 0; /* Align container to the left */
    top: 0; /* Align container to the top */
    width: 100%; /* Set width to 100% for responsiveness */
    height: auto; /* Allow height to adjust based on content */
    padding-top: calc(200 / 480 * 100%); /* Set aspect ratio (200px height and 480px width) */
    background-color: lightgray; /* Adding background color for visualization */
    overflow: hidden; /* Hide overflow to prevent horizontal scrollbar */
  }
  .textbox {
    width: calc(70 / 480 * 100%); /* Set width as percentage of container width */
    height: calc(66 / 200 * 100%); /* Set height as percentage of container height */
    margin-right: calc(10 / 480 * 100%); /* Set margin as percentage of container width */
    text-align: center;
    font-size: calc(55 / 480 * 100vw); /* Set font size as percentage of viewport width */
    font-family: 'Roboto Condensed', sans-serif; /* Changing font to Roboto Condensed */
    font-weight: 800; /* Setting font weight to Ultra-Bold */
    color: black;
    border: none; /* Remove borders */
    appearance: none; /* Remove arrows */
    outline: none; /* Remove outline */
    margin-bottom: 0; /* Adjust position */
    margin-top: 0; /* Align at top */
    background-color: lightblue; /* Adding background color for visualization */
    box-sizing: border-box; /* Ensure padding and border are included in width */
  }
  .textbox:focus {
    outline: none; /* Ensure no outline on focus */
  }
  .textbox:first-child {
    background-color: black;
    color: white;
  }
  #imageContainer {
    position: absolute;
    top: 0;
    right: 0; /* Stick image to the right */
    width: auto; /* Allow width to adjust based on content */
    height: 100%; /* Set height to 100% of container height */
    pointer-events: none; /* Initially disable pointer events */
    background-color: black; /* Set image container back to black */
    opacity: 1; /* Start with opacity 1 */
    transition: opacity 2s; /* Add transition for opacity */
  }
  #listenerBoxImage {
    width: auto; /* Allow the width to adjust based on the image's natural size */
    height: 100%; /* Set the height to 100% of the container's height */
    max-width: 100%; /* Limit the width to 100% of the container's width */
    object-fit: contain; /* Maintain aspect ratio and fit the entire image within the container */
    filter: brightness(0);
    font-family: 'Roboto', sans-serif;
    font-weight: 800;
    letter-spacing: 5px; /* Add letter-spacing */
    transition: filter 2s; /* Add transition for filter */
    background-color: red; /* Adding background color for visualization */
  }
  #numberDisplay {
    margin-top: calc(20 / 200 * 100%); /* Set margin as percentage of container height */
    font-size: calc(18 / 480 * 100vw); /* Set font size as percentage of viewport width */
    opacity: 0;
    transition: opacity 2s;
    font-family: 'Roboto', sans-serif;
    font-weight: 800;
    letter-spacing: 5px; /* Add letter-spacing */
    transition-delay: 2s; /* Delay the transition for 2 seconds */
    background-color: red; /* Adding background color for visualization */
  }
  #whatsappLink {
    margin-top: calc(10 / 200 * 100%); /* Set margin as percentage of container height */
    font-size: calc(16 / 480 * 100vw); /* Set font size as percentage of viewport width */
    display: none;
  }

  /* Chrome, Safari, Edge, Opera */
  input::-webkit-outer-spin-button,
  input::-webkit-inner-spin-button {
    -webkit-appearance: none;
    margin: 0;
  }

  /* Firefox */
  input[type=number] {
    -moz-appearance: textfield;
  }

  /* Additional text box style */
  #specialTextbox {
    position: absolute;
    width: calc(70 / 480 * 100%); /* Set width as percentage of container width */
    height: calc(66 / 200 * 100%); /* Set height as percentage of container height */
    bottom: 0; /* Align at bottom */
    left: calc(36 / 480 * 100%); /* Set left position as percentage of container width */
    transform: translateX(-50%);
    background-color: black;
    color: white;
    font-family: 'Roboto Condensed', sans-serif;
    font-weight: 800;
    text-align: center;
    pointer-events: none; /* Disable pointer events */
    display: flex;
    align-items: center; /* Center text vertically */
    justify-content: center; /* Center text horizontally */
    letter-spacing: 5px; /* Set kerning to 5 */
    font-size: calc(22 / 480 * 100vw); /* Set font size as percentage of viewport width */
  }

  /* Style for the black rectangle */
  #blackRectangle {
    position: absolute;
    left: 0; /* Align rectangle to the left of the container */
    top: 0; /* Align rectangle to the top of the container */
    width: calc(72 / 480 * 100%); /* Set width as percentage of container width */
    height: 100%; /* Set height to 100% of container height */
    background-color: black; /* Set background color to black */
    z-index: 0; /* Ensure the rectangle is behind all other elements */
  }

  /* Pink container style */
  #pinkContainer {
    position: absolute; /* Position the container */
    left: 0; /* Align container to the left */
    top: 0; /* Align container to the top */
    width: 100%; /* Set width to 100% */
    padding-top: calc(284 / 480 * 100%); /* Set aspect ratio (284px height and 480px width) */
    background-color: pink; /* Set background color to pink */
    z-index: -1; /* Ensure the pink container is behind all other elements */
    border: 1px solid red; /* Add 1px red border */
    box-sizing: border-box; /* Ensure padding and border are included in width */
  }
</style>
</head>
<body>

<div class="container">
  <div id="blackRectangle"></div> <!-- Add the black rectangle inside the container -->
  <form id="textBoxForm">
    <input type="text" class="textbox" maxlength="2" id="box1">
    <input type="number" class="textbox" maxlength="2" id="box2">
    <input type="number" class="textbox" maxlength="2" id="box3">
    <input type="number" class="textbox" maxlength="2" id="box4">
    <input type="number" class="textbox" maxlength="2" id="box5">
    <input type="number" class="textbox" maxlength="2" id="box6">
    <input type="number" class="textbox" maxlength="2" id="box7" oninput="this.value = this.value.slice(0, 2)">
  </form>
  <div id="specialTextbox">MO</div> <!-- Added special textbox -->
  <a id="imageContainer" href="#" target="_blank">
    <img id="listenerBoxImage" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhWXXS_Ck4r3a39lSm3py19uGIjOCrCVTB2dFy42uP3J0vOA4G1fjgOi9iuY8GXiTMzdAU5gzZK5ozsmmf4mp2OEby0WuSZII2vlaQKaqvcjgUaKlocRQUSxwps2ScI3vgKOREgxb-V7QgvMm69EBjZsIvJnQJZzMaZHasby8pfJFV1X12FurRPTJmIjJHd/s1062/IMG_3581%20(1).jpg" alt="Listener Box Image">
  </a>
</div>

<div id="numberDisplay"></div>

<!-- Pink container -->
<div id="pinkContainer"></div>

<script>
  // Function to set position and size of a textbox
  function setTextBoxStyle(textboxId, position, size, left, top) {
    var textbox = document.getElementById(textboxId);
    if (textbox) {
      textbox.style.position = position;
      textbox.style.width = size.width;
      textbox.style.height = size.height;
      textbox.style.left = left;
      textbox.style.top = top;
    }
  }

 // Example: Move box1 to be 20px from the left of the container and 20px from the top
  setTextBoxStyle("box1", "absolute", { width: "calc(70 / 480 * 100%)", height: "calc(66 / 200 * 100%)" }, "1px", "0px");
  setTextBoxStyle("box2", "absolute", { width: "calc(70 / 480 * 100%)", height: "calc(66 / 200 * 100%)" }, "calc(89 / 480 * 100%)", "0px");
  setTextBoxStyle("box3", "absolute", { width: "calc(70 / 480 * 100%)", height: "calc(66 / 200 * 100%)" }, "calc(194 / 480 * 100%)", "0px");
  setTextBoxStyle("box4", "absolute", { width: "calc(70 / 480 * 100%)", height: "calc(66 / 200 * 100%)" }, "calc(89 / 480 * 100%)", "calc(67 / 200 * 100%)");
  setTextBoxStyle("box5", "absolute", { width: "calc(70 / 480 * 100%)", height: "calc(66 / 200 * 100%)" }, "calc(194 / 480 * 100%)", "calc(67 / 200 * 100%)");
  setTextBoxStyle("box6", "absolute", { width: "calc(70 / 480 * 100%)", height: "calc(66 / 200 * 100%)" }, "calc(89 / 480 * 100%)", "calc(134 / 200 * 100%)");
  setTextBoxStyle("box7", "absolute", { width: "calc(70 / 480 * 100%)", height: "calc(66 / 200 * 100%)" }, "calc(194 / 480 * 100%)", "calc(134 / 200 * 100%)");
  // Similarly, set position and size for other textboxes as needed

  var boxes = document.querySelectorAll('.textbox');
  var numberDisplay = document.getElementById('numberDisplay');
  var listenerBoxImage = document.getElementById('listenerBoxImage');
  var imageContainer = document.getElementById('imageContainer');
  var totalDigits = 0;

  for (var i = 0; i < boxes.length; i++) {
    boxes[i].addEventListener('input', function(event) {
      if (this.value.length == this.maxLength) {
        var nextBox = this.nextElementSibling;
        if (nextBox && nextBox.type === "number") {
          nextBox.focus();
        }
        totalDigits = calculateTotalDigits();
        if (totalDigits == 231) {
          updateNumberDisplay();
        }
      }
    });
  }

  function calculateTotalDigits() {
    var total = 0;
    for (var i = 0; i < boxes.length; i++) {
      total += parseInt(boxes[i].value);
    }
    return total;
  }

  function updateNumberDisplay() {
    var number = '';
    for (var i = 0; i < boxes.length; i++) {
      number += boxes[i].value;
    }
    var formattedNumber = number.slice(0, 2) + '°' + number.slice(2, 4) + '\'' + number.slice(4, 6) + '.' + number.slice(6, 7) + '”S, ' + number.slice(7, 9) + '°' + number.slice(9, 11) + '\'' + number.slice(11, 13) + '.' + number.slice(13, 14) + '”E';
    numberDisplay.textContent = formattedNumber;
    numberDisplay.style.opacity = 1;
    setTimeout(function() {
      // Start both animations once all digits are filled
      fadeInListenerBox();
      fadeInImage();
    }, 2000); // Delay for 2 seconds before displaying the WhatsApp link
  }

  function fadeInListenerBox() {
    var currentOpacity = 0;
    var interval = 2000 / 20; // 20 steps for a 2-second animation
    var opacityStep = 1 / 20; // Opacity change per step
    var fadeInterval = setInterval(function() {
      currentOpacity += opacityStep;
      listenerBoxImage.style.filter = 'brightness(' + currentOpacity + ')';
      if (currentOpacity >= 1) {
        clearInterval(fadeInterval);
        var formattedNumber = '';
        for (var i = 0; i < boxes.length; i++) {
          formattedNumber += boxes[i].value;
        }
        formattedNumber = formattedNumber.slice(0, 2) + '°' + formattedNumber.slice(2, 4) + '\'' + formattedNumber.slice(4, 6) + '.' + formattedNumber.slice(6, 7) + '”S, ' + formattedNumber.slice(7, 9) + '°' + formattedNumber.slice(9, 11) + '\'' + formattedNumber.slice(11, 13) + '.' + formattedNumber.slice(13, 14) + '”E';
        var shareURL = 'https://wa.me/?text=▮%20e%20m%20e%20r%20g%20e%20n%20t%20%20%20l%20a%20n%20d%20m%20a%20r%20k%20%20%20|%20%20*SNOWFLAKE*%0A%0Ahttps://www.google.com/maps?q=' + encodeURIComponent(formattedNumber.replace(/\s+/g, ''));
        listenerBoxImage.parentElement.setAttribute('href', shareURL);
        imageContainer.style.pointerEvents = 'auto'; // Enable pointer events after fading in
      }
    }, interval);
  }

  function fadeInImage() {
    setTimeout(function() {
      listenerBoxImage.style.filter = 'brightness(1)'; // Set brightness to normal
      imageContainer.style.opacity = 1;
    }, 2000); // Delay for 2 seconds before starting the fade-in animation
  }
</script>

</body>
</html>
