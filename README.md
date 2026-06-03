<!DOCTYPE html>
<html>
<head>
<style>
body {
    margin: 0;
    background: transparent;
    overflow: hidden;
}

#text {
    font-family: Arial, sans-serif;
    font-size: 32px;
    color: black;
    white-space: nowrap;
}
</style>
</head>
<body>

<div id="text"></div>

<script>
const lyrics = [
    "I want to kiss you, ugh",
    "Baby likes it messy",
    "And she loves to cause a scene.",
    "Touchin' me in public.",
    "Like she wants the world to see."
];

let lyricIndex = 0;
let charIndex = 0;
let deleting = false;
const text = document.getElementById("text");

function animateText() {
    const current = lyrics[lyricIndex];

    if (!deleting) {
        text.textContent = current.substring(0, charIndex + 1);
        charIndex++;

        if (charIndex === current.length) {
            deleting = true;
            setTimeout(animateText, 1200);
            return;
        }
    } else {
        text.textContent = current.substring(0, charIndex - 1);
        charIndex--;

        if (charIndex === 0) {
            deleting = false;
            lyricIndex = (lyricIndex + 1) % lyrics.length;
        }
    }

    setTimeout(animateText, deleting ? 50 : 80);
}

animateText();
</script>

</body>
</html>
