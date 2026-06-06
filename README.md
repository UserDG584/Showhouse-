// =========================================
// SHOWHOUSE DG FRONTEND
// =========================================

const SCRIPT_URL =
"https://script.google.com/macros/s/YOUR_DEPLOYMENT_ID/exec";

// -----------------------------------------
// SEND SURVEY EMAIL
// -----------------------------------------

async function sendSurveyEmail() {

```
const email =
document.getElementById("customerEmail")
.value
.trim();

if(!email){

    alert(
    "Please enter an email address."
    );

    return;

}

try{

    const response =
    await fetch(
    SCRIPT_URL,
    {
        method:"POST",

        headers:{
            "Content-Type":
            "application/x-www-form-urlencoded"
        },

        body:
        new URLSearchParams({

            action:"sendSurvey",

            email:email

        })

    });

    if(response.ok){

        document.getElementById("status")
        .innerHTML =
        "Survey sent successfully.";

    }

}
catch(error){

    console.error(error);

    alert(
    "Unable to send survey."
    );

}
```

}

// -----------------------------------------
// SUBMIT CRM SURVEY
// -----------------------------------------

async function submitSurvey(event){

```
event.preventDefault();

const form =
document.getElementById("quoteForm");

const formData =
new FormData(form);

const extras =
Array.from(
    document.querySelectorAll(
        ".extras:checked"
    )
)
.map(
    checkbox => checkbox.value
);

let extrasValue =
"None";

if(extras.length){

    extrasValue =
    extras.join(" + ");

}

const allSelected =

extras.includes("F") &&
extras.includes("S") &&
extras.includes("SP") &&
extras.includes("xSML") &&
extras.includes("xM/L");

if(allSelected){

    extrasValue =
    "All";

}

formData.append(
    "extrasCombined",
    extrasValue
);

try{

    const response =
    await fetch(
        SCRIPT_URL,
        {
            method:"POST",
            body:formData
        }
    );

    if(response.ok){

        window.location.href =
        "thankyou.html";

    }

}
catch(error){

    console.error(error);

    alert(
    "Unable to submit survey."
    );

}
```

}

// -----------------------------------------
// CONDITIONAL QUESTIONS
// -----------------------------------------

document.addEventListener(
"DOMContentLoaded",
function(){

const otherGlass =
document.getElementById(
"otherGlass"
);

if(otherGlass){

otherGlass.addEventListener(
"change",
function(){

document.getElementById(
"otherGlassDescription"
).style.display =

this.value === "Yes"
? "block"
: "none";

});

}

const conservatory =
document.getElementById(
"conservatory"
);

if(conservatory){

conservatory.addEventListener(
"change",
function(){

document.getElementById(
"conservatoryDescription"
).style.display =

this.value === "Yes"
? "block"
: "none";

});

}

});
