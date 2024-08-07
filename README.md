# resume-claw-machine
claw machine resume
cd resume-claw-machine
touch index.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Resume Claw Machine</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <h1>Leilani I. Torres Resume Claw Machine</h1>
    <div id="claw-machine">
        <div id="claw"></div>
        <div id="prizes">
            <div class="prize" data-category="education">Education</div>
            <div class="prize" data-category="experience">Experience</div>
            <div class="prize" data-category="achievements">Achievements</div>
            <div class="prize" data-category="skills">Skills</div>
        </div>
    </div>
    <div id="info-display">
        <button id="try-again">Try Again</button>
        <div id="info-content"></div>
    </div>
    <script src="script.js"></script>
</body>
</html>
touch style.css
body {
    font-family: Arial, sans-serif;
    text-align: center;
    background-color: #f0f0f0;
}

h1 {
    margin-top: 20px;
}

#claw-machine {
    position: relative;
    width: 300px;
    margin: 50px auto;
    border: 2px solid #000;
    height: 300px;
    background-color: #fff;
}

#claw {
    position: absolute;
    top: 0;
    left: 50%;
    width: 50px;
    height: 50px;
    background-color: red;
    transform: translateX(-50%);
    transition: top 1s;
}

#prizes {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    display: flex;
    justify-content: space-around;
    padding: 10px;
}

.prize {
    width: 60px;
    height: 60px;
    background-color: #4caf50;
    color: #fff;
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;
}

#info-display {
    display: none;
    margin-top: 20px;
}

#info-content {
    background-color: #fff;
    padding: 20px;
    border: 2px solid #000;
    width: 300px;
    margin: 0 auto;
    text-align: left;
}

#try-again {
    margin-top: 20px;
}
touch script.js
const claw = document.getElementById('claw');
const prizes = document.querySelectorAll('.prize');
const infoDisplay = document.getElementById('info-display');
const infoContent = document.getElementById('info-content');
const tryAgainButton = document.getElementById('try-again');

const resumeData = {
    education: `<h2>Education</h2>
                <p><strong>Bachelor of Mechanical Engineering</strong><br>
                Florida Atlantic University, Boca Raton, FL<br>
                Expected Graduation: January 2024</p>
                <p><strong>Bachelor of Finance</strong><br>
                Florida Atlantic University, Boca Raton, FL<br>
                Graduated: May 2023</p>
                <p><strong>High School Diploma</strong><br>
                Royal Palm Beach Community High School<br>
                Graduated: May 2018</p>`,
    experience: `<h2>Experience</h2>
                <p><strong>Math Interventionist</strong><br>
                Somerset Wellington Academy, Wellington, FL<br>
                August 2022 – September 2023</p>
                <p><strong>Sales Associate</strong><br>
                Target, Royal Palm Beach, FL<br>
                July 2021 – August 2022</p>`,
    achievements: `<h2>Achievements</h2>
                <p>Hackathon Participation: Participated in [Hackathon Name]</p>
                <p>Dean's List: Consistently achieved Dean's List recognition for academic excellence.</p>`,
    skills: `<h2>Skills</h2>
            <p>Technical Skills: MATLAB, SolidWorks, Microsoft Excel, CAD, 3D modeling</p>
            <p>Mathematics: Engineering Mathematics, Calculus III</p>
            <p>Soft Skills: Quick learner, Natural leader, Organized, Accountable, Detail oriented, Collaborative</p>`
};

prizes.forEach(prize => {
    prize.addEventListener('click', () => {
        const category = prize.getAttribute('data-category');
        claw.style.top = '80%';
        setTimeout(() => {
            claw.style.top = '0';
            displayInfo(category);
        }, 1000);
    });
});

tryAgainButton.addEventListener('click', () => {
    infoDisplay.style.display = 'none';
    document.getElementById('claw-machine').style.display = 'block';
});

function displayInfo(category) {
    infoContent.innerHTML = resumeData[category];
    infoDisplay.style.display = 'block';
    document.getElementById('claw-machine').style.display = 'none';
}
git add .
git commit -m "Initial commit"
git push origin main

