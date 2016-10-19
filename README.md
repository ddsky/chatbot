# chatbot
A simple chat bot in JavaScript with links to smart conversational APIs such as [WebKnox](https://webknox.com/api) (all purpose question answering), [spoonacular](https://spoonacular.com/food-api) (food related conversations), and [DuckDuckGo Instant Answers](https://duckduckgo.com/api) (mostly entities like movies, people, and places).

## Demo

Take a look at the JavaScript Chat Bot using the Duck Duck Go Engine: [Demo](http://rawgit.com/ddsky/chatbot/master/demo/demo.html)

## Set up HTML
    <div id="chatBotCommandDescription"></div>
    <input id="humanInput" type="text" />
    <div id="chatBot">
        <div id="chatBotThinkingIndicator"></div>
        <div id="chatBotHistory"></div>
    </div>

## Sample Usage
    // initialize the bot
    var config = {
        // what inputs should the bot listen to? this selector should point to at least one input field
        inputs: '#humanInput',
        // if you want to show the capabilities of the bot under the search input
        inputCapabilityListing: true,
        // optionally, you can specify which conversation engines the bot should use, e.g. webknox, spoonacular, or duckduckgo
        engines: [ChatBot.Engines.duckduckgo()]
    };
    ChatBot.init(config);
        
    // give your bot a name
    ChatBot.setBotName("bender");
        
    //// manually define some patterns
    // 1. parameter: the pattern to listen for
    // 2. parameter: either "response" to respond or "rewrite" to rewrite the request
    // 3. parameter: either the response or the rewrite value, or undefined if nothing should happen
    // 4. parameter: a callback function that gets the matches of the pattern
    // 5. parameter: a description of that pattern, this is used to tell the user what he can say. Use quotes '' to mark phrases and [] to mark placeholders
    ChatBot.addPattern(
        "(?:my name is|I'm|I am) (.*)",
        "response",
        "Hi $1, thanks for talking to me today", 
        function(matches){
            ChatBot.setHumanName(matches[1]);
        },
        "Say 'My name is [name]' to be called by your name."
    );        
    
    ChatBot.addPattern("^hi$","response","Howdy my friend", undefined, "Say 'Hi' to be greeted.");
    
    ChatBot.addPattern(
        "compute ([0-9]+) plus ([0-9]+)", 
        "response", 
        undefined, 
        function (matches) {
            ChatBot.addChatEntry("That would be "+(1*matches[1]+1*matches[2])+".","bot");
        },
        "Say 'compute [number] plus [number]' to make the bot your math monkey"
    );
    
    
    

    
   