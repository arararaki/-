# -
程式設計 期中
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <!-- The above 3 meta tags *must* come first in the head; any other head content must come *after* these tags -->
    <meta name="description" content="">
    <meta name="author" content="">
    <link rel="icon" href="favicon.ico">
    <title>Jumbotron Template for Bootstrap</title>
    <!-- Bootstrap core CSS -->
    <link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.5/css/bootstrap.min.css" rel="stylesheet">
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.5/css/bootstrap-theme.min.css"></script>
<style>
/* Move down content because we have a fixed navbar that is 50px tall */
body {
  padding-top: 60px;
  padding-bottom: 20px;
  } 
marquee {
  padding-top:80px;
  }

</style>
  </head>

  <body background="CNsdU.jpg"　text="#000000"　link="#0066cc"　vlink="#336600">
    <nav class="navbar navbar-inverse navbar-fixed-top">
      <div class="container">
        <div class="navbar-header">
          <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#navbar" aria-expanded="false" aria-controls="navbar">
            <span class="sr-only">Toggle navigation</span>
            <span class="icon-bar"></span>
            <span class="icon-bar"></span>
            <span class="icon-bar"></span>
          </button>
          <a class="navbar-brand" href="#">留言板</a>
        </div>
        <div id="navbar" class="navbar-collapse collapse">
        </div><!--/.navbar-collapse -->
      </div>
    </nav>

    <div class="container">
      <!-- Example row of columns -->
      <div class="row">
        <div class="col-md-4">
        </div>
        <div class="col-md-4">
          <form class="form-signin">
             <label align="left" for="title" class="sr-only">標題</label><br/>
             <input type="text" id="title" class="form-control" placeholder="標題" required autofocus><br/>
             <textarea  class="form-control" rows="5" id="text" placeholder="內文"></textarea><br/>
             <button class="btn btn-lg btn-primary btn-block" type="submit" onclick="save()">儲存</button>
          </form>
          <table id="list"></table>
          <button onclick="del()">清除留言</button>
        </div>
        <div class="col-md-4">
        </div>
      </div> 
      <footer>
       <marquee behavior="alternate" direction="left" >歡迎蒞臨本站</marquee>
        </footer>
    </div> <!-- /container -->


    <!-- Bootstrap core JavaScript
    ================================================== -->
    <!-- Placed at the end of the document so the pages load faster -->
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.5/js/bootstrap.min.js"></script>
        <script>
var oTitle = document.getElementById("title");
var oText  = document.getElementById("text");
var oList = document.getElementById("list");

function save() {
  var title = oTitle.value;
  var text  = oText.value;
  window.localStorage.setItem("notepad:"+title, text);
  showList();
}

function showList() {
  var rowHtml = "";
  for (var title in window.localStorage) {
    if (title.startsWith("notepad:")) {
      rowHtml += "<tr><td><a onclick=\"loadDoc('"+title+"')\">"+title.substring(8)+"</a></td></tr>"
    }
  }
  oList.innerHTML = rowHtml;
}

function loadDoc(title) {
  oTitle.value = title.substring(8);
  oText.value  = window.localStorage.getItem(title);
}
function del() {
  var title = oTitle.value;
  var text  = oText.value;
  window.localStorage.clear("notepad:"+title, text);
  showList();
}


</script>
  </body>
</html>
