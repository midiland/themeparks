# wdwJS

An unofficial API library for accessing Disney park wait times, opening times and other information from the Disney API.

# Install

    npm install wdwjs
  
# Example Use

    // Setup API
    var DisneyAPI = new (require("wdwjs"))({
        timeFormat: "HH:mm"
    });

    var MagicKingdom = DisneyAPI.MagicKingdom;
    
    // Get Magic Kingdom wait times
    MagicKingdom.GetWaitTimes(function(err, data) {
        if (err) return console.error("Error fetching Magic Kingdom wait times: " + err);
        
        console.log(JSON.stringify(data, null, 2));
    });
    
    // Get Magic Kingdom opening times
    MagicKingdom.GetSchedule(function(err, data) {
        if (err) return console.error("Error fetching Magic Kingdom schedule: " + err);

        console.log(JSON.stringify(data, null, 2));
    });

    // Parks available
    //  ** Disney World **
    //  DisneyAPI.MagicKingdom
    //  DisneyAPI.Epcot
    //  DisneyAPI.AnimalKingdom
    //  DisneyAPI.HollywoodStudios
    //
    //  ** Disney California **
    //  DisneyAPI.Disneyland
    //  DisneyAPI.CaliforniaAdventure
    //
    //  ** Disney Paris **
    //  DisneyAPI.DisneylandParis
    //  DisneyAPI.WaltDisneyStudios


# API Options

    var DisneyAPI = new (require("wdwjs"))({
        // turn on debug logging
        //  defaults: false
        debug: false,
        // time format for any times returned by the API
        //  see MomentJS docs for format options http://momentjs.com/docs/#/displaying/format/
        timeFormat: "YYYY-MM-DDTHH:mm:ssZ",
        // date format for any dates returned by the API
        dateFormat: "YYYY-MM-DD"
    });

# Advanced Use (Disney World / California APIs only)    

    // Get an API page using an ID and type
    DisneyAPI.GetPage(80010208, "Attraction", function(error, data) {
        console.log(JSON.stringify(data, null, 2));
    });
    
    // Get a specific API URL
    DisneyAPI.GetURL("https://api.wdpro.disney.go.com/global-pool-override-B/facility-service/theme-parks/80007944", function(e, data) {
       console.log(JSON.stringify(data, null, 2));
    });

# Acknowledgments

Based on code from lloydpick/echelon https://github.com/lloydpick/echelon/

# TODO

Currently missing ride opening/closing times on WDW rides
Currently missing park opening/closing times for EuroDisney