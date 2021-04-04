---
title: Site Search
layout: search
---
<section><div><form action="/search" method="get"><label for="q">Search sembcorpenergy.co.uk:</label><input style="width: 65%;display:inline;margin-right:12px;" type="search" id="q" name="q" size="30"><input class="btn" type="submit" value="Search"><input type="hidden" id="start" name="start" value="1"></form></div></section><br/>
<div id="searchResult"><br/><br/><br/><br/><br/><br/><br/><br/>S E A R C H I N G . . .  <br/><br/><br/><br/><br/><br/><br/><br/></div>
<div id="searchNav"></div>

<script nonce='quasidolphineggcupelectricity'>
function reqListener() {
  var data = JSON.parse(this.responseText);
  var searchresulthtml = '';
  var searchNavhtml = '';
  //console.log(data);
  searchresulthtml = searchresulthtml + '<div>Results for Search Term "'+data.searchTerms+'"</div><br/>'
  for( item in data.items){
  searchresulthtml = searchresulthtml + '<div><a href="'+data.items[item].link+'">'+data.items[item].title+'</a><p>'+data.items[item].snippet+'</p></div>';
  }
  document.getElementById("searchResult").innerHTML = searchresulthtml;

  if(data.previousPage){searchNavhtml = searchNavhtml + '<a href="/search?q='+data.searchTerms+'&start='+data.previousPage+'"><button class="btn">Previous results</button></a>&nbsp;'}
  if(data.nextPage){searchNavhtml = searchNavhtml + '&nbsp;<a href="/search?q='+data.searchTerms+'&start='+data.nextPage+'"><button class="btn">Next results</button></a>'}
  document.getElementById("searchNav").innerHTML = searchNavhtml;
}

function reqError(err) {
  console.log('Fetch Error :-S', err);
}
var qstring = '?q=Energy&start=1'
if(window.location.search){
qstring = window.location.search
}
var oReq = new XMLHttpRequest();
oReq.onload = reqListener;
oReq.onerror = reqError;
oReq.open('get', 'https://europe-west2-xousian.cloudfunctions.net/site-search'+qstring, true);
oReq.send();
</script>

