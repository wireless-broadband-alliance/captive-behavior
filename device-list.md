## Device Database

<link href="/assets/css/tidy-table.css" rel="stylesheet" type="text/css">
<script src="/assets/scripts/tidy-table.min.js"></script>
<script>

// Define top level table columns here, no spaces
var columns= [
  'DeviceCode',
  'DeviceName', 
  'DeviceManufacturer',
  'DeviceType',
  'WlanType',
  'WlanFreq2.4G',
  'WlanFreq5g',
  'WlanFreq6',
  'CNADoc',
  'PasspointR2Capable'
];

var formatted_columns = []
for(var i=0; i< columns.length; i++){
  formatted_columns.push( displayCamelCase(columns[i]) );
}

function displayCamelCase (str){
  result = str.replace( /([A-Z])/g, " $1" );
  return result.charAt(0).toUpperCase() + result.slice(1);
}

function prepareRow (obj) {
  var tableRow = [];  
  for( var i=0; i < columns.length; i++) {
    var col = columns[i];
    if( col in obj){
      tableRow.push(obj[col])  
    }
    else {
      tableRow.push(false)
    }
  }
  return tableRow;
}

// checkmarks and x marks
function postProcessTableData(elem){
  
  var element_value = elem.getAttribute('title');

  if(element_value === "true" ){
    elem.innerHTML = '<span class="checkmark">&#10003;</span>'
  }
  else if ( element_value === "false" ){
    elem.innerHTML = '<span class="x-mark">&#10007;</span>';
  }
  else if ( element_value.startsWith("/") ){
  	elem.innerHTML = '<a href="' + element_value + '" target="_blank">Link</a>';
  }
  
}

function buildTable(data, containerId){
 
// Prepare Data
 var tableData = [];
  for( var i=0; i < data.length; i++){
    tableData.push( prepareRow(data[i]) );
  }

// Build tidy table
document.getElementById(containerId)
 .TidyTable({
   enableCheckbox: false,
   enableMenu:     false,
   responsive:     true
 },
 {
   columnTitles: formatted_columns,
   columnValues: tableData,
  
  // post-process DOM elements
  postProcess: {
    column: postProcessTableData
  },

   // pre-process column values before sort (optional)
   sortByPattern: function(col_num, val) {
     if (col_num != 1) return val;

     return String(val).replace(/$|%|#/g, '');
   }
 });
}

// Main page load event
window.addEventListener('load', function() {

	var request = new XMLHttpRequest();
	request.open('GET', '/assets/data/devices.json', true);

	request.onload = function() {
	  if (request.status >= 200 && request.status < 400) {
	    // Success!
	    var data = JSON.parse(request.responseText);
	    buildTable(data, "container");
	  } else {
	    // We reached our target server, but it returned an error
	    console.log("Could not retrieve devices JSON file")
	  }
	};

	request.onerror = function() {
	  // There was a connection error of some sort
	   console.log("Connection error")
	};

	request.send();
});
</script>

<div id="container"></div>