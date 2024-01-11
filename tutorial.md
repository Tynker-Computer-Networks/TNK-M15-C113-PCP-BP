Tambola Stage-1
==================


In this activity, you will learn to create the login screen for the players to join the online tambola game.


<img src= "https://media.slid.es/uploads/1525744/images/8813171/prjct.png" width = "480" height = "320">


Follow the given steps to complete this activity:


1. Resize the canvas to full screen.


* Open the file `client.py`.
* Replace the fixed values of canvas width and height i.e. 600 and 400 with screen_width and screen_height respectively in the ask_player_name() method.
~~~python
canvas1 = Canvas( name_window, width = screen_width, height = screen_height)
~~~


2. Create a save_name() method to fetch the player’s information, encode it, and send it to the server.


* Define the method save_name().
~~~python
def save_name():
    global SERVER, player_name, name_window, name_entry
    player_name = name_entry.get()
    name_entry.delete(0, END)
    name_window.destroy()
    SERVER.send(player_name.encode())
)
~~~


3. Fetch the player information and store it on the server.


* Open the file `server.py`.


* Fetch the player_name from the player_socket, decode it, and store it in a player_name variable.
~~~python
player_name = player_socket.recv(1024).decode().strip()
~~~
 
* Create an empty dictionary and save it under player_name key in CLIENTS
~~~python
CLIENTS[player_name] = {}
~~~


* Store the socket, address, and player_name in the dictionary.
~~~python
CLIENTS[player_name]["player_socket"] = player_socket
CLIENTS[player_name]["address"] = addr
CLIENTS[player_name]["player_name"] = player_name
~~~  


* Print all the clients information.
~~~python
print(f"Clients : {CLIENTS}")
~~~


* Save and run the code to check the output.


