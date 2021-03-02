<!DOCTYPE html>

<html lang="en">

<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1" />
<style type="text/css">
html {height: 100%;}
body {
	background-repeat: no-repeat;
	background-attachment: fixed;
	height: 100%;
	min-height: 100%;
	margin: 0;
	
	background: rgb(238,238,238); /* Old browsers */
	/* IE9 SVG, needs conditional override of 'filter' to 'none' */
	background: url(data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiA/Pgo8c3ZnIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgd2lkdGg9IjEwMCUiIGhlaWdodD0iMTAwJSIgdmlld0JveD0iMCAwIDEgMSIgcHJlc2VydmVBc3BlY3RSYXRpbz0ibm9uZSI+CiAgPGxpbmVhckdyYWRpZW50IGlkPSJncmFkLXVjZ2ctZ2VuZXJhdGVkIiBncmFkaWVudFVuaXRzPSJ1c2VyU3BhY2VPblVzZSIgeDE9IjAlIiB5MT0iMCUiIHgyPSIwJSIgeTI9IjEwMCUiPgogICAgPHN0b3Agb2Zmc2V0PSIwJSIgc3RvcC1jb2xvcj0iI2VlZWVlZSIgc3RvcC1vcGFjaXR5PSIxIi8+CiAgICA8c3RvcCBvZmZzZXQ9IjEwMCUiIHN0b3AtY29sb3I9IiNjY2NjY2MiIHN0b3Atb3BhY2l0eT0iMSIvPgogIDwvbGluZWFyR3JhZGllbnQ+CiAgPHJlY3QgeD0iMCIgeT0iMCIgd2lkdGg9IjEiIGhlaWdodD0iMSIgZmlsbD0idXJsKCNncmFkLXVjZ2ctZ2VuZXJhdGVkKSIgLz4KPC9zdmc+);
	background: -moz-linear-gradient(top,  rgba(238,238,238,1) 0%, rgba(204,204,204,1) 100%); /* FF3.6+ */
	background: -webkit-gradient(linear, left top, left bottom, color-stop(0%,rgba(238,238,238,1)), color-stop(100%,rgba(204,204,204,1))); /* Chrome,Safari4+ */
	background: -webkit-linear-gradient(top,  rgba(238,238,238,1) 0%,rgba(204,204,204,1) 100%); /* Chrome10+,Safari5.1+ */
	background: -o-linear-gradient(top,  rgba(238,238,238,1) 0%,rgba(204,204,204,1) 100%); /* Opera 11.10+ */
	background: -ms-linear-gradient(top,  rgba(238,238,238,1) 0%,rgba(204,204,204,1) 100%); /* IE10+ */
	background: linear-gradient(to bottom,  rgba(238,238,238,1) 0%,rgba(204,204,204,1) 100%); /* W3C */
	filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#eeeeee', endColorstr='#cccccc',GradientType=0 ); /* IE6-8 */
}
h1 {
	font-family: Arial, Helvetica, sans-serif;
	color: #962300;
	font-size: 25px;
}
p {
	font-family: Arial, Helvetica, sans-serif;
	color: #777;
	font-size: 12px;
}
#bloctxt {
	border-left-width: 5px;
	border-left-style: solid;
	border-left-color: #962300;
	padding-left: 10px;
	position: absolute;
	top:5%;
	left: 50%;
	width: 600px;
	margin-left: -260px
}
#wrapper {
	padding: 10px;
	margin: 0 auto;
}
#border {
	background-color: #99C;
	border: 1px solid #B90000;
	-webkit-border-radius: 7px;
	-moz-border-radius: 7px;
	border-radius: 7px;
	margin: 0 auto;
	padding: 5px;
	width:800px;
	height:800px;
}

#canvas {
	width:800px; 
	height:800px;
}

#MMFCanvas {
	-webkit-box-shadow:  0px 0px 4px 4px rgba(0, 0, 0, 0.25); 
    box-shadow:  0px 0px 4px 4px rgba(0, 0, 0, 0.25);
}
</style>

  <title>Clickteam Fusion 2.5 HTML5 Runtime</title>

	<script>
	   	// Detection of old browsers that do not support the canvas element
		// Falls back to a default page
	    if (!document.createElement("canvas").getContext)
	    {
			window.open("http://www.clickteam.com/html5-fallback", "_self");
		}
	</script>
	
  	<!-- EXTRASOURCES -->
	<!-- Loads the Javascript code...-->
  	<script src="src/Runtime.js"></script>
  	
    <script>
	// Detects if the html file is ran locally.
	// You can remove this code for the final version
	if (window.location.protocol == "file:")
	{
		document.write('<div id="bloctxt">');
		document.write('<h1>The application cannot be run...</h1>');
		document.write('<p>HTML browsers do not allow you to launch data files directly from the file system.<br>');
		document.write('A drag & drop of the html file on a web-browser window will not work, on any machine.<br>');
		document.write('Please use the Build & Run option (it opens a local web server) to run your application,<br>') 
		document.write('or upload your application folder to a remote web-server, and start it from there...</p>');
		document.write('</div>');
		throw new error("Cannot run application");
	}
    </script>

</head>

<!-- This is where we create the Canvas element that will contain the application...-->
<body>

    <div id="wrapper">
	    <div id="border">
		    <div id="canvas">
			    <canvas id="MMFCanvas" width="800" height="800">
				    <p>Your browser does not support Canvas.</p>
			    </canvas>   
		    </div>
	    </div>
    </div>  
    <script>
        window.rs = "src/Runtime.js";
        window.fs = "624396";
    </script>
    <script>
	    // RUNTIMESTART
	    // This is where the HTML5 runtime is actually started
	    window.addEventListener("load", windowLoaded, false);
	    function windowLoaded()
	    {
		    // Calls the runtime
		    // First parameter : name of the canvas element
		    // Second parameter : path to the cch file. Images and sounds must lay beside this file
		    new Runtime("MMFCanvas", "resources/Application 1.cch");
	    }
	    // RUNTIMESTARTEND
    </script>

    <p align="center">Clickteam Fusion 2.5 HTML5 template.</p>
    <!-- Clickteam logo, encoded within the html code.-->  
    <div align="center"><a href="http://www.clickteam.com"><img src="data:image/png;base64,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"></a></div> 
</body>
</html>
