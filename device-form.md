## Device Form

<link rel="stylesheet" style="text/css" href="/assets/css/bootstrap.css" />
<form style="max-width:500px; margin: 0px auto;"></form>
<div id="res" class="alert"></div>
<script type="text/javascript" src="/assets/scripts/jquery.min.js"></script>
<script type="text/javascript" src="/assets/scripts/underscore.js"></script>
<script type="text/javascript" src="/assets/scripts/jsv.js"></script>
<script type="text/javascript" src="/assets/scripts/jsonform.js"></script>
<script type="text/javascript">
$('form').jsonForm({
  schema: {
        "DeviceCode":
        {
            "type": "string",
            "title": "Device Code",
            "description":"The specific hardware model identifier from the device manufacturer, e.g. 'IPHONE12,5'"
        },
        "DeviceName":
        {
            "type": "string",
            "title": "Device Name",
            "description":"The friendly name of the device, e.g. 'iPhone 11 Pro Max'"
        },
        "DeviceManufacturer":
        {
            "type": "string",
            "title": "Device Manufacturer",
            "enum": [ "--","Apple Inc.", "Google", "Samsung", "Dell", "Huawei", "LG", "Motorola" ]
        },
        "DeviceOperatingSystem":
        {
            "type": "string",
            "title": "Device Operating System",
            "enum": [ "--","iOS", "iPadOS", "Android", "Windows", "macOS", "Linux", "Other" ]
        },
        "DeviceOperatingSystemMajorVersion":
        {
            "type": "string",
            "title": "Device Operating System Major Version",
            "description":"The numbered operating system major version of the OS selected above, e.g. '13' for iOS13, or '10' for Windows 10. Please use the number rather than the name, e.g. '10.15' instead of 'macOS Catalina'." 
        },
        "DeviceOperatingSystemMinorVersion":
        {
            "type": "string",
            "title": "Device Operating System Version",
            "description":"The numbered operating system minor version of the OS selected above, e.g. '13.5' for iOS13, or '10.0' for Windows 10. Please use the number rather than the name, e.g. '10.15.1' instead of 'macOS Catalina'." 
        },      
        "DeviceType":
        {
            "type": "string",
            "title": "Device Type",
            "enum": [ "--","Mobile Phone", "Tablet", "Laptop Computer", "Wearable", "Gaming Console", "E-reader", "Other"]
        },
        "CNASupport":
        {
          "type": "string",
          "title": "Captive Network Assistant Support",
          "enum": [
              "Not Supported",
              "Supported, Closes Automatically After Authentication",
              "Supported, Stays Open After Authentication",
            ]
        },
        "CapPortSupport":
        {
          "type": "array",
          "title": "Capport API Support",
          "items": {
            "type": "string",
            "title": "Select one or more",
            "enum": [
              "Not Supported",
              "Venue URL Supported",
              "Time Left Supported",
              "Extend Session Supported",
              "Other"
            ]
          }
        },
        "MACRandomization": {
          "type": "array",
          "title": "Default MAC Randomization Behavior",
          "items": {
            "type": "string",
            "title": "Select one or more",
            "enum": [
              "None",
              "When Scanning",
              "When Connecting, Unique Per SSID",
              "When Connecting, Unique Per Session",
              "When Connecting, Unique Per Time Period",
              "Other"
            ]
          }
        },
        "Comments":
        {
            "type": "string",
            "title": "Additional Comments",
            "description":"If you have addtional information you want us to capture you can put that here." 
        }        
    },
  form : [
      "*",
      {
        "type": "actions",
        "items": [
          {
            "type": "submit",
            "title": "Submit"
          }
        ]
      }
  ],
  onSubmit: function (errors, values) {
    if (errors) {
      $('#res').html('<p>Errors found.</p>');
    }
    else {
      $('#res').html('<p>' + values.DeviceCode + ' Submitted.');
      $('form').hide();
      //console.log(JSON.stringify(values));

      $.ajax({
        type: "POST",
        url: "https://u5qjgjp6y2.execute-api.eu-west-2.amazonaws.com/dbd",
        data: JSON.stringify(values),
        success: function(){
          console.log("Success");
        },
        dataType: "json"
      });
    }
}});
</script>