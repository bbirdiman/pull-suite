# pull-suite

#### simple javascript routine to pull files from a remote .epub.

this is code i wrote
to show some people
that they don't know
what they're talking about.


````
<!doctype html><html><head><meta charset="utf-8">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black">
<meta name="format-detection" content="telephone=no">
<meta name=viewport content="width=device-width, user-scalable=no, user-scalable=0, initial-scale=1, minimum-scale=1, maximum-scale=1">
<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
<title>pull files from a remote .epub</title>
<script type="text/javascript" src="http://stuk.github.io/jszip/dist/jszip.js"></script>
<script type="text/javascript" src="http://stuk.github.io/jszip-utils/dist/jszip-utils.js"></script>
<!-- mandatory in the scumbags, ie 6, 7, 8 and 9. -->
<!--[if IE]>
<script type="text/javascript" src="http://stuk.github.io/jszip-utils/dist/jszip-utils-ie.js"></script>
<![endif]-->
<script type="text/javascript" src="http://stuk.github.io/jszip/test/jquery-1.8.3.min.js"></script>
</head>
<body style=padding-left:30px;background-color:orange;overflow-x:hidden;overflow-y:scroll>
<h1>pull files from a remote .epub</h1>
<div id="theoutput" style=background-color:honeydew;padding-left:30px></div>
<! ------------------------------- scripts start here -------------------------------- -->
<script>
JSZipUtils.getBinaryContent('http://zenmagiclove.com/simple/suite.epub', function(err, data) {
try {
var zip = new JSZip(data)
var moby=zip.file("suite.opf").asText()
var opf=zip.file("suite.opf").asText();opf=opf.replace(/</g,"&lt;")
var ncx=zip.file("suite.ncx").asText();ncx=ncx.replace(/</g,"&lt;")
var firstchapter=zip.file("suite-chapter_1_--_the_chunk_is_the_basic_unit.html").asText()
firstchapter=firstchapter.replace(/</g,"&lt;").replace(/\n\n\n\n\n/g,"\n\n")
var secondchapter=zip.file("suite-chapter_2_--_chunks_are_stored_in_gourds.html").asText()
secondchapter=secondchapter.replace(/</g,"&lt;").replace(/\n\n\n\n\n/g,"\n\n")
var content="<hr><hr><hr><hr>"+"<h2>opf:</h2><pre>\n"+opf+"</pre>"+"\n<hr><hr><hr><hr>"
content=content+"<h2>ncx:</h2><pre>\n"+ncx+"</pre>"+"<hr><hr><hr><hr>"
content=content+"<h2>chapter 1:</h2><pre>\n"+firstchapter+"</pre>"+"<hr><hr><hr><hr>"
content=content+"<h2>chapter 2:</h2><pre>\n"+secondchapter+"</pre>"+"<hr><hr><hr><hr>"
$("#theoutput").html(content)
} catch(e) {$("#theoutput").html("<h1>oops, there was an error -- "+e+"</h1>")}
})
</script>
</body>
</html>

````
