
<!DOCTYPE html>
<html>
<head>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title> Weather App - Easy Tutorials</title>
<link rel="stylesheet" href="style.css">
</head>
<body>

    <div class="card">
    <div class="search">

        <input type="text" id="city" placeholder="Enter city name" spellcheck="false">
<button> <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSyi_CVTmoL1ITHFxQkfLwvj93hcsgA1Olkhg&s" style="width: 20px; height: 20px;"></button>
    </div>
    <div class="error">
        <p>Invalid </p>
    </div>
    <div class="Weather">
        <img src="https://cdn-icons-png.flaticon.com/512/6142/6142570.png" class="weather-icon" style="width: 200px; height: 250px;">
        <h1 class="temp">22°C</h1>
        <h2 class="city" > New York</h2>
        <div class="details">
            <div class="col">
                <img src="https://cdn-icons-png.freepik.com/256/7614/7614405.png?semt=ais_hybrid" style="width: 50px; height: 50px;">

                <div>
                    <p class="humidity">50%</p>
                    <p>humidity</p>
                    </div>
                    </div>
                    <div class="col">
                        <img src="https://cdn-icons-png.flaticon.com/512/4834/4834507.png"style="width: 50px; height: 50px;">
                        <div>
                            <p class="wind">10km/h</p>
                            <p>wind speed</p>
                            </div>
                            </div>
            </div>
        </div>
</div>

<script> 

const apiKey = "5b1112495dbef260ec08d56ab3413bc8";
const apiUrl = "https://api.openweathermap.org/data/2.5/weather?units=metric&q=";

const searchBox = document.querySelector(".search input");
const searchBtn = document.querySelector(".search button");
const weatherIcon = document.querySelector(".weather-icon");

async function CheckWeather(city){
    const respons = await fetch(apiUrl + city + `&appid=${apiKey}`);
    if(respons.status == 404) {
        document.querySelector(".error").style.display = "block";
        document.querySelector(".weather").style.display = "none";
    }else{

    }
var data = await respons.json();

document.querySelector(".city").innerHTML = data.name;
document.querySelector(".temp").innerHTML = Math.round(data.main.temp) + "°C";
document.querySelector(".humidity").innerHTML = data.main.humidity  + "%";
document.querySelector(".wind").innerHTML = data.wind.speed + "km/h" ;

if(data.weather[0].main == "cloud"){
    weatherIcon.src = "cloud.png.png";
}
else if(data.weather[0].main == "clear"){
    weatherIcon.src = "clear.png.webg";
}
else if(data.weather[0].main == "Rain"){
    weatherIcon.src = "rain.png.png";
}

else if(data.weather[0].main == "Drizzle"){
    weatherIcon.src = "drizzle.png.png";
}

else if(data.weather[0].main == "Mist"){
    weatherIcon.src = "mist.png.png";
}
    
    
    document.querySelector(".weather").style.display = "block";

    document.querySelector(".error").style.display = "none";

    }
    
searchBtn.addEventListener("click",()=>{
    CheckWeather(searchBox.value);
}) 
</script>
</body>
</html>
# st
