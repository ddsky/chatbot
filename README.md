# chatbot
A simple chat bot in JavaScript with links to smart conversational APIs such as [WebKnox](https://webknox.com/api) (all purpose question answering), [spoonacular](https://spoonacular.com/food-api) (food related conversations), and [DuckDuckGo Instant Answers](https://duckduckgo.com/api) (mostly entities like movies, people, and places).

## Demo

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
        // optionally, you can specify which conversation engines the bot should use, e.g. webknox, spoonacular, or duckduckgo
        engines: [ChatBot.Engines.duckduckgo()]
    };
    ChatBot.init(config);
        
    // give your bot a name
    ChatBot.setBotName("bender");
        
    // manually define some patterns
    ChatBot.addPattern("^hi$","response","hi yourself", undefined, "Say 'Hi' to be greeted.");
    
    // you can also add callbacks
    ChatBot.addPattern(
        "(?:my name is|I'm|I am) (.*)",
        "response",
        "hi $1, thanks for talking to me today", 
        function(matches){
            ChatBot.setHumanName(matches[1]);
        },
        "Say 'My name is [name]' to be called by your name."
    );
    

    
   