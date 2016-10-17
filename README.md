# chatbot
A simple chat bot in JavaScript with links to smart APIs.

## Set up HTML
    <div id="chatBot">
        <div id="chatBotThinkingIndicator"></div>
        <div id="chatBotHistory"></div>
    </div>

## Sample Usage

    // give your bot a name
    ChatBot.setBotName("bender");
        
    // manually define some patterns
    ChatBot.addPattern("^hi$","response","hi yourself");
    
    // you can also add callbacks
    ChatBot.addPattern(
        "(?:my name is|I'm|I am) (.*)",
        "response",
        "hi $1, thanks for talking to me today", 
        function(matches){
            ChatBot.setHumanName(matches[1]);
        }
    );
    

    
   