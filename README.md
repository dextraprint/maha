
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
	<meta name="viewport" content="width=device-width, initial-scale=1">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
    <title>save segment</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link rel="stylesheet" href="style.css">
	<link rel="stylesheet" href="//code.jquery.com/ui/1.12.1/themes/base/jqueryui.css">
   <script src="https://code.jquery.com/jquery-1.12.4.js"></script>
   <script src="https://code.jquery.com/ui/1.12.1/jquery-ui.js"></script>
	
</head>
<body>
    <main>
        <section>
            <h1 class="text-center" style="color:#fff"><b>Form</b></h1>
            <hr width="50px">
        <!-- Modal Link Container -->
            <div class="container">
                <a href="#modal1" class="modal-btn">Save Segment</a>
            </div>
        <!-- End of Modal Link Container -->
        </section>
    </main>
    <!-- Modal Sample #1 -->
    <div id="modal1" class="modal">
        <div class="modal-container">
            <div class="modal-header">
                <h3><strong>Popup</strong></h3>
                <a href="#" class="btn-close">&times;</a>
            </div>
            <div class="modal-body">
              
	
<div class="text-align:right;">
</div>
<br>

<br>
	 

 <form id="your-form-id">
<div class="dropdown">
<div id="myDropdown" class="dropdown-content">
<br>
<!-- 
 <a href="url" onclick="myFunction()" id="Data" class="dropbtn">&#43; Add a New Schema</a>

 <label for="myDropdown">Add schema to segment</label>
	 
	  

<select id="myDropdown">
  <option label="First Name" value="first_name"></option>
  <option label="Last Name" value="last_name"></option>
  <option label="Gender" value="gender"></option>
  <option label="Age" value="age"></option>
  <option label="Account Name" value="account_name"></option>
  <option label="City" value="city"></option>
  <option label="State" value="state"></option>
  
  
    <select id="myDropdown">
  <option label="First Name" value="first_name"></option>
  <option label="Last Name" value="last_name"></option>
  <option label="Gender" value="gender"></option>
  <option label="Age" value="age"></option>
  <option label="Account Name" value="account_name"></option>
  <option label="City" value="city"></option>
  <option label="State" value="state"></option>
</select>
  
</select>  

        <div class="row">
  <div class="customer_records">
    <input name="first_name" type="text" value="name">
	  <input name="age" type="number" value="age">
	
	<a class="extra-fields-customer" href="#">&#43; Add a New Schema Segment</a>
  
<div class="customer_records_dynamic"></div>
    
  </div>

  

</div>


<br>
<br>
<br>
<button onclick="displayName()"> Save the segment</button>
<button onclick="displayName()"> Cancel</button>
   <p id="show_name"></p>
 </div>
</div>
<br>
<br>
<br>
       
-->
<form class="form-horizontal" >
  <div class="form-group">
    <div class="col-sm-10">
	<br>
	  <br>	  
<div id="segment-popup" class="popup">
    <label class="control-label col-sm-2" for="email">Enter the Name of the Segment</label>

    <input type="text" id="segment-name" placeholder="Segment Name">
		  <p>To save Your Segment, you need to add the schemas to build the query</p>
	
    <select id="add-schema-dropdown">
        <option value="first_name">First Name</option>
        <option value="last_name">Last Name</option>
		<option value="gender">Gender</option>
		<option value="age">Age</option>
		<option value="account_name">Account Name</option>
		<option value="city">City</option>
		<option value="state">State</option>
		
	
		
        <!-- Add other schema options here -->
    </select>
    <a href="#" id="add-new-schema">+ Add new schema</a>
    <!-- The blue box for added schemas will go here -->
	<br>
	<br>
	<br>
    <div id="blue-box"></div>
    <button id="save-segment">Save the Segment</button>
	    <button id="cancel">Cancel</button>

</div>

    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
<script>
$(document).ready(function () {
    const $segmentPopup = $("#segment-popup");
    const $addSchemaDropdown = $("#add-schema-dropdown");
    const $addNewSchema = $("#add-new-schema");
    const $blueBox = $("#blue-box");

    // Click event handler for "Save Segment" button
    $("#save-segment-btn").click(function () {
        $segmentPopup.show();
    });

    // Click event handler for "+ Add new schema" link
    $addNewSchema.click(function (e) {
        e.preventDefault();
        const selectedOption = $addSchemaDropdown.find(":selected");
        if (selectedOption.length > 0) {
            const newSchemaDropdown = $("<select>");
            // Populate the new dropdown with unselected options
            $addSchemaDropdown.find("option").not(":selected").each(function () {
                newSchemaDropdown.append($("<option>", {
                    value: $(this).val(),
                    text: $(this).text()
                }));
            });
            $blueBox.append(newSchemaDropdown);
        }
    });

    // Click event handler for "Save the Segment" button
    $("#save-segment").click(function () {
        const segmentName = $("#segment-name").val();
        const selectedSchemas = [];
        $blueBox.find("select").each(function () {
            selectedSchemas.push({
                [$(this).val()]: $(this).find(":selected").text()
            });
        });

        // Prepare the data object
        const data = {
            segment_name: segmentName,
            schema: selectedSchemas
        };alert(JSON.stringify(data));

        // Send data to the server using AJAX or Fetch API
        $.ajax({
            url: "https://webhook.site/your-webhook-url", // Replace with your webhook URL
            type: "POST",
            data: JSON.stringify(data),
            contentType: "application/json",
            success: function (response) {
                console.log("Data sent successfully:", response);
            },
            error: function (error) {
                console.error("Error sending data:", error);
            }
        });
    });
});
</script>
</body>
</html>
<body>
<!--
   <input type="text" placeholder="enter your name" id="txtInputData"> </input>
   <p id="show1_name"></p>-->

</body>
</form>

</html>
	  
    </div>
  </div>
  </form>
        </div>
    </div>

</body>
</html>
</body




