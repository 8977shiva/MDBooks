```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Ajax</title>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
  </head>
  <body>
    <div id="container">
      <div id="output"></div>
      <ul id="user"></ul>
      <h3>Post Form</h3>
      <form id="postForm" action="http://localhost:3000/api/post">
        <input type="text" id="title" placeholder="Title" /><br />
        <textarea name="body" id="body" cols="30" rows="10"></textarea><br />
        <input type="submit" />
      </form>
    </div>

    <script>
      $(document).ready(() => {
        //load
        $("#output").load("test1.html", (respone, status, xhr) => {
          if (status === "success") {
            console.log("success");
          } else if (status == "error") {
            console.log("error:" + JSON.stringify(xhr));
            alert(xhr.statusText);
          }
        });
        // get
        $.get("test.html", (data) => {
          $("#output").html(data);
        });
        getJSON;
        $.getJSON("https://jsonplaceholder.typicode.com/users", (data) => {
          $.each(data, (idx, val) => {
            $("ul#user").prepend("<li>" + val.name + "</li>");
          });
        });
        // ajax
        $.ajax({
          method: "GET",
          url: "https://jsonplaceholder.typicode.com/users",
          dataType: "json",
        })
          .done((data) => {
            $.each(data, (idx, val) => {
              $("ul#user").prepend("<li>" + val.name + "</li>");
            });
          })
          .fail(function (xhr, status, errorThrown) {
            alert("Sorry, there was a problem!");
            console.log("Error: " + xhr.statusText);
          });

        //post
        $("#postForm").submit((e) => {
          e.preventDefault();
          let title = $("#title").val();
          let body = $("body").val();
          let url = $(this).attr("action");

          $.post(url, { title: title, body: body })
            .done((data) => {
              console.log("post Saved");
              console.log(data);
            })
            .fail(function (xhr, status, errorThrown) {
              alert("Sorry, there was a problem!");
              console.log("Error: " + xhr.statusText);
            });
        });
      });
    </script>
  </body>
</html>

```



##    effects

```html
<!DOCTYPE hmtl>
<html>
  <head>
    <!-- <link href="style.css" rel="stylesheet" type="text/css" /> -->
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
    <style>
      #box {
    background: #333;
    color: #fff;
    width: 500px;
    height: 90px;
    text-align: center;
    padding: 20px;
}

#box2 {
    background: red;
    width: 100px;
    height: 100px;
    position: relative;
}
    </style>
  </head>
  <body>
    <header><h1>jQuery Effects</h1></header>
    <h3>Fade</h3>
    <div id="container">
      <button id="btnFadeOut">Fade Out</button>
      <button id="btnFadeIn">Fade In</button>
      <button id="btnFadeTol">Fade Toggle</button>
    </div>
    <hr />
    <h3>Slide</h3>
    <div id="container">
      <button id="btnSlideUp">Slide Up</button>
      <button id="btnSlideDown">Slide Down</button>
      <button id="btnSlideTog">Slide Toggle</button>
      <button id="btnStop">Stop</button>
    </div>
    <hr />

    <div id="box"><h1>Hello World</h1></div>
    <hr />
    <h3>Animate</h3>
    <div id="container">
      <button id="btnMoveLeft">Move let</button>
      <button id="btnMoveRight">Move Right</button>
      <button id="btnMoveAround">Move Around</button>
    </div>
    <hr />
    <div id="box2"></div>
    <script >
      $(document).ready(function () {
  //fadeOut
  $("#btnFadeOut").click(function () {
    $("#box").fadeOut();
  });
  //fadeIn
  $("#btnFadeIn").click(function () {
    $("#box").fadeIn();
  });
  //fadeToggle
  $("#btnFadeTol").click(function () {
    $("#box").fadeToggle();
  });
  // Slide up
  $("#btnSlideUp").click(() => {
    $("#box").slideUp(3000);
  });
  $("#btnSlideDown").click(() => {
    $("#box").slideDown(3000);
  });
  $("#btnSlideTog").click(() => {
    $("#box").slideToggle(3000);
  });
  $("#btnStop").click(() => {
    $("#box").stop(3000);
  });
});

//Animate
$(document).ready(() => {
  $("#btnMoveLeft").click(() => {
    $("#box2").animate({
      left: 0,
    });
  });
  $("#btnMoveRight").click(() => {
    $("#box2").animate({
      left: 300,
    });
  });
});

    </script>
  </body>
</html>

```

