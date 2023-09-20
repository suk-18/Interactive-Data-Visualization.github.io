# Interactive-Data-Visualization

This project is a simple web application which allows the users to interactively visualize the data sets in more proper manner.It is developed with the help of HTML,CSS ans JS.
This application uses the Chart.js library for the creation of line chart and such data is represented as JSON object.The application also uses the Anime.js library which adds interesting animations to the project.

## Explanation of Code 

The main functionality of the application is added in the file named as index.js which holds the JS code. This code is further divided into three parts as follows:

1.The code imports all the necessary libraries.

2.The code creates the line charts.

3.The code creates the animations.

### Importing the Libraries

The following libraries are imported by the first part of the code.The libraries are as follows:

1.Chart.js

2.Anime.js

## HTML

```

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Interactive-Data-Visualization</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <div class="chart-container">
      <canvas id="myChart"></canvas>
    </div>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/3.7.0/chart.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/animejs/3.2.1/anime.min.js"></script>
    <script src="index.js"></script>
  </body>
</html>

```

## CSS

```

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
 background-color: azure;
  
}
.chart-container {
  max-width: 600px;
  margin: 0 auto;
  
}

```

## JS

```

const data = {
  labels: [
    "Monday",
    "Tuesday",
    "Wednesday",
    "Thursday",
    "Friday",
    "Saturday",
    "Sunday",
  ],
  datasets: [
    {
      label: "Monthly Employee Presents",
      backgroundColor: "rgba(75, 192, 192, 0.2)",
      borderColor: "rgba(75, 192, 192, 1)",
      borderWidth: 1,
      data: [65, 59, 80, 81, 56, 40, 30],
    },
  ],
};
const config = {
  type: "bar",
  data: data,
  options: {
    responsive: true,
    plugins: {
      title: {
        display: true,
        text: "Monthly Employee Data",
      },
    },
  },
};
const ctx = document.getElementById("myChart").getContext("2d");
const myChart = new Chart(ctx, config);
myChart.options.plugins.tooltip = {
  callbacks: {
    label: function (context) {
      return `Sales: ${context.parsed.y}`;
    },
  },
};
const chartAnimation = anime({
  targets: myChart.data.datasets[0].data,
  easing: "linear",
  delay: anime.stagger(200),
  duration: 1000,
  loop: true,
  direction: "alternate",
  update: function (anim) {
    myChart.update();
  },
});

```

**Hosted Link**: https://suk-18.github.io/Interactive-Data-Visualization.github.io/
