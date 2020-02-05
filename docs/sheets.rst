Google Sheets
=============

you can poll a variable and store the results

Google Sheets. Tools > Script editor, new, paste
::

    function collectData()
    {
        var  sheet = SpreadsheetApp.getActiveSheet();

        var response = UrlFetchApp.fetch("https://api.particle.io/v1/devices/<device_id>/JSON_status?access_token=<auth_token>");

        try
        {
            var response = JSON.parse(response.getContentText()); // parse the JSON the Particle API created
            var JSON_status = unescape(response.result); // unescape before your parse as JSON

            try
            {
                var p = JSON.parse(JSON_status); // parse the JSON you created
                var datum = new Date(); // time stamps are always good when taking readings
                sheet.appendRow([datum, p.Strength, p.Quality, p.FreeMem, p.Temp1, p.Temp2, p.Humi, p.Dew, p.DewAlert, p.Light, p.Dust, p.CO2, p.TSTATon, p.MOV1, p.MOV1light, p.MOV2, p.MOV2light, p.BEAMalert, p.BEAMlight, p.SUNLight, p.Night, p.Bed, p.R, p.G, p.B]); // append the specified data to the sheet
            } catch(e)
            {
                Logger.log("Unable to do second parse");
            }
        } catch(e)
        {
            Logger.log("Unable to returned JSON");
        }
    }
