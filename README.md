<script>
  //Use a timer to keep checking for a completed action from another dialog
  var theTimer;

  window.setTheTimer = function() {
    //To Do - Hide the Spinner
    if (typeof(Storage) === "undefined") {
      alert('HTML5 Storage is not supported.  This Add-on will not work in this browser.  Please update your browser.');
      return;
    }

    try {
    window.sessionStorage.setItem("new_value","n"); //Make sure check value is reset
    } catch(e) {
      alert(e.error + ' You may have this apps cookies blocked in this browser, and/or this browser tab.  Check cookie blocking.');
      return;
    };
    theTimer = window.setInterval(monitorForTheResponse, 500); //Every 1/2 second, check for response value
  };

  window.monitorForTheResponse = function() {
    var wuzSbmtid,dlgInfo;
    wuzSbmtid = window.sessionStorage.getItem("new_value");
    if (wuzSbmtid === 'y') {//Dialog just wrote value to window.sessionStorage
      window.sessionStorage.setItem("new_value","n");//Reset
      clearTimeout(theTimer);//turn off timer
      //Get submitted values
      dlgInfo = window.sessionStorage.getItem("DataDrktr_pckedInfo");

      //To Do - Run code to display new value
    };
  };
</script>
