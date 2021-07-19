
# Arras Mayhem
The offical client for the arras-mayhem server.

![Purple Arras.io logo](https://cdn.glitch.com/fca666a2-8235-47b6-a711-c9926dc2248f%2FLogo.png?v=1595837913869) 
[![Netlify Status](https://api.netlify.com/api/v1/badges/ee4ba925-dbe8-40fd-9faf-83e3dabe4b5b/deploy-status)](https://app.netlify.com/sites/arras-moe/deploys) [![Official Discord server](https://discordapp.com/api/guilds/427668515357458443/embed.png)](https://discord.gg/yTZdDPA)

# Features
- Sound effects!
- Music!
- Lightweight, separate client! 
- More colours!
- Server Selector!
- More themes!
- Fixed hotkeys! (Be sure your server project has them binded)
- Deployment to Repl.it or Heroku! Still works with Glitch!
- Webserver compatibility with 6 different languages!
- In-game Chat! 
- *boing boing*
> :warning: **Chat system requires server modification!!!**<br/> It won't work out of the box with standard servers, minor code additions are needed, scroll down for the tutorial!


# Trailer
[![kute trailer](http://img.youtube.com/vi/P3cuHSb8Ols/0.jpg)](https://www.youtube.com/watch?v=P3cuHSb8Ols "arras mayhem")
# Webservers
The client is able to be hosted as either a Node.js Express, PHP, Go HTTP, Ruby Webrick, C or Python Flask webserver. Details below! Examples are linked as well.

- Node.JS Express server:
   ``node index.js``
    - <https://repl.it/@umineko/arras-express> 
    - <https://gitlab.com/seaguli/arras-express>
- PHP webserver: 
   ``php -S 0.0.0.0:8000 -t`` 
   - <https://repl.it/@umineko/arras-php>
- Python Flask server:
   ``python main.py`` 
   - <https://repl.it/@umineko/arras-flask>
   - <https://gitlab.com/seaguli/arras-flask>
- Go HTTP server: 
   ``go build`` , then ``./main``
   - <https://repl.it/@umineko/arras-go>
   - <https://gitlab.com/seaguli/arras-go>
- Ruby Webrick server:
   ``ruby main.rb`` 
   - <https://repl.it/@umineko/arras-ruby>
   - <https://gitlab.com/seaguli/arras-ruby>
- C webserver: 
   ``make`` , then ``./arras 8000 ./``
   - <https://repl.it/@umineko/arras-C>
   
Additonal code is available on my Github project's page, <https://github.com/seaguli/arras-mayhem>
# Remixing
Feel free to remix this project and modify it to your own liking! You aren't required to credit me, but I would like it :D

<sub><sup>
    ask me if you want any aspect of the server's code at (SF) Seagull#2224
</sub></sup>
# Setting it up
Thanks to [MG] Octo#9071 for the server selector and guide!
## How to add your server(s)
- Go to line 3339 in bundle.js
- You'll see there are multiple things that look like this:
```
          {
            visible: 0,
            id: "1",
            type: "game",
            code: "glitch-worldwide-f",
            at: p.glitch('your-server'),
            prefer: !0,
           // featured: 1, // For Featured Status.
          },
```
- Now, lets break it down. The first thing you'll see is `visable 0,`. Don't worry, it is.
- The next thing is id. This is what will appear in the web address. I like to have them start at 1 and numarically have them go up
- The thing after that is "type". This is used for indentifying the gamemode but it doesnt really matter what you put in cuase it wont effect the game, only the server does that
- Under that, is `code: "glitch-worldwide-f",`. This effects how it'll show in the server selector. Lets break this down too.
- First of all, it sais "glitch". This is the server provider your using. Say if your using Heroku instead, you would put Heroku
- After that it sais "worldwide". This is the region. Just keep it at worldwide unless your really gonna set up servers in different locations
- at the end, it sais "f". This is the gamemode that displays in the server selector. Here is a list of gamemodes you can choose from
- (note; This is just what it displays, if you want it to actally be say domination, you gotta do that in your server code.)
```
p=private
e=word
w=words
o=open
m=maze
f=ffa
2=2TDM
3=3TDM
4=TDM
d=domination
m=mothership
a=assault
```
- Next we got ``at: p.glitch('your-server'),``. This is where you'll put in to connect to your server.
- The p.glitch is what server hoster its gonna attempt to connect to. If we want heroku, we would put in p.heroku instead of p.glitch.
- Afterwards, theres ``prefer: !0,``. I wouldnt mess with it but it makes you automaiticly connect to that server by default
- Horray! You are now done doing the informational reading. Lets put this knowledge into use.
- What were gonna try to do;
- Have a server that connects to my glitch server that is 2TDM.
- The first thing were gonna do is find the server selector code in bundle.js on line 3339.
- Next, where gonna look at the code and figure out what to do.
```
          {
            visible: 0,
            id: "1",
            type: "game",
            code: "glitch-worldwide-f",
            at: p.glitch('your-server'),
            prefer: !0,
           // featured: 1, // For Featured Status.
          },
```
- Now that you are there, lets edit some things. 
- We want to connect to our glitch project, "swift-checkered-wildebeest".
- What where gonna do is replace the "your-server" with "swift-checkered-wildebeest".
- After that, were gonna change ``code: "glitch-worldwide-f",`` to ``code: "glitch-worldwide-2"``. 
- What i did is this: Keep it as glitch cause thats what where using; Keep at as worldwide cause why not; replace the "f" with "2" becuase we want 2TDM. Remember, a list of all the gamemodes is listed above.
- And there we go, we should know have a working, custom client with a server selector! Horray!
# Domains
The client can be found at the following links:

- <https://arras-mayhem.glitch.me>
- <https://arras-moe.glitch.me>
- <https://arras.neocities.org>
- <https://arras-mayhem.netlify.app/>
- <https://arras-mayhem.vercel.app/>
- <https://seaguli.github.io/arras-mayhem/> (Styleless version)
- <https://arras-mayhem.umineko.repl.co/> (Does not recieve client updates)

# Chat System Tutorial

**Add the code below to your server for the chat system to function!**

 First, you should find this code block:
   
     case "S":
            {
              // clock syncing
              if (m.length !== 1) {
                socket.kick("Ill-sized sync packet.");
                return 1;
              }
              // Get data
              let synctick = m[0];
              // Verify it
              if (typeof synctick !== "number") {
                socket.kick("Weird sync packet.");
                return 1;
              }
              // Bounce it back
              socket.talk("S", synctick, util.time());
            }
            break;
Copy this code, which contains the main chat system and commands, paste it above the aforementioned code snippet         
```
///////////////////////COPY CODE BELOW!!!///////////////
          case "h":
            if (!socket.status.deceased) {
              // Chat system!!.

              let message = m[0];
              let maxLen = 100;
              let args = message.split(" ");
              if (message.startsWith("/")) {
                //help command
                if (message.startsWith("/help")) {
                  player.body.sendMessage(
                  player.body.sendMessage("/km ~ Destroys your tank");
                  return 1;
                }
                // suicide command
                if (message.startsWith("/km")) {
                  {
                    player.body.destroy();
                    return 1;
                  }
                } else
                  return player.body.sendMessage(
                    "Invalid command. Run /help for a list of commands."
                  );
              }
              if (util.time() - socket.status.lastChatTime >= 2200) {
                // Verify it
                if (typeof message != "string") {
                  player.body.sendMessage("Invalid chat message.");
                  return 1;
                }
 
                if (encodeURI(message).split(/%..|./).length > maxLen) {
                  player.body.sendMessage(
                    "Your message is too long. (<100 Characters)"
                  );
                  return 1;
                }
  
                let playerName = socket.player.name
                  ? socket.player.name
                  : "Unnamed";
                let chatMessage = playerName + " says: " + message;
                sockets.broadcast(chatMessage);
                util.log("[CHAT] " + chatMessage);
                // Basic chat spam control.
                socket.status.lastChatTime = util.time();
              } else
                player.body.sendMessage("You're sending messages too quickly!");
            }
            break;
```
your code should be looking like this now

      
               case "h":
            if (!socket.status.deceased) {
              // Chat system!!.

              let message = m[0];
              let maxLen = 100;
              let args = message.split(" ");
              if (message.startsWith("/")) {
                //help command
                if (message.startsWith("/help")) {
                  player.body.sendMessage("/km ~ Destroys your tank");
                  return 1;
                }
                // suicide command
                if (message.startsWith("/km")) {
                  {
                    player.body.destroy();
                    return 1;
                  }
                } else
                  return player.body.sendMessage(
                    "Invalid command. Run /help for a list of commands."
                  );
              }
              if (util.time() - socket.status.lastChatTime >= 2200) {
                // Verify it
                if (typeof message != "string") {
                  player.body.sendMessage("Invalid chat message.");
                  return 1;
                }
 
                if (encodeURI(message).split(/%..|./).length > maxLen) {
                  player.body.sendMessage(
                    "Your message is too long. (<100 Characters)"
                  );
                  return 1;
                }
  
                let playerName = socket.player.name
                  ? socket.player.name
                  : "Unnamed";
                let chatMessage = playerName + " says: " + message;
                sockets.broadcast(chatMessage);
                util.log("[CHAT] " + chatMessage);
                // Basic chat spam control.
                socket.status.lastChatTime = util.time();
              } else
                player.body.sendMessage("You're sending messages too quickly!");
            }
            break;
          case "S":
            {
              // clock syncing
              if (m.length !== 1) {
                socket.kick("Ill-sized sync packet.");
                return 1;
              }
              // Get data
              let synctick = m[0];
              // Verify it
              if (typeof synctick !== "number") {
                socket.kick("Weird sync packet.");
                return 1;
              }
              // Bounce it back
              socket.talk("S", synctick, util.time());
            }
            break;

then you should find this 

     socket.status = {
          verified: false,
          receiving: 0,
          deceased: true,
          requests: 0,
          hasSpawned: false,
          needsFullMap: true,
          needsNewBroadcast: true,
          lastHeartbeat: util.time(),
        };      
add this below *lastHeartbeat: util.time(),*

`        lastChatTime: util.time()`
  
  Then you should find this code block

     // Free the old view
              if (views.indexOf(socket.view) != -1) {
                util.remove(views, views.indexOf(socket.view));
                socket.makeView();
              }
              socket.player = socket.spawn(name);

add this below *socket.player = socket.spawn(name);*
` socket.player.name = name;`

**And voila! Your chat system is working! This assumes you are remixing my client, which already has all the client-side code needed for the chat to function!**

# Credits
- Original Client by ProKameron
<https://glitch.com/~imp-template2>
- Seaguli
- Powfu [MG] Octo#9071
- Various StackOverflow contributors (For webserver code)
- CX and the various developers of arras.io

