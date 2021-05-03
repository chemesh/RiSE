# RiSE
RiSE (Ritzpa Stock Exchange) is a stock trading simulator written in java, given as a project as part of my computer science Bs.c degree  

RiSE_v1 – Ritzpa Stock Exchange version 1.0

Overview:
This program was written and made as the first part of the Java Project “RSE” given along with the course.
“RiSE” is a stock exchange framework to use in order to deal and trade with various stocks information, which is uploaded to the system via a dedicated interface.
This part of the project is a first out of 3, which implements a trading engine as the program main backbone, and a console user interface to navigate through the system and make use of the engine capabilities.
To run “RiSE”, double click “RiSE.bat”
Bonus Implemented – support “MKT trade order”

How-to-use:
After running RiSE.bat, the console application should appear.
This program will display its outputs only after an agreement from the user, interpreted by pressing the Enter button on your keyboard.
For any incorrect/mishandled input by the user, “RiSE” will produce a message informing the user on the issue, and returning to the main menu.
For every first run it is needed to upload a valid XML file built in accordance to RSE-V1.xsd Schema. this could be done by selecting the 1st option in the main menu, and directing the program to the xml file by typing in the file’s full path.
If the xml file is corrupted or invalid for some reason, it’s contents wouldn’t be
uploaded to system, and a dedicated message error would appear on the
console.

After loading the xml data, “RiSE” is ready for use. This operation can be made at any given moment, resetting the current stock and trading data in the system. 
System data wouldn’t reset after uploading a malfunctioned xml file. 

Options 2 and 3 would provide the user with shallow data on the stocks in the system,  and a thorough information on a single stock, respectively.

Option 4 is for making an active trade order to be sent and processed by the system. Current possible trade order types are “LMT” and “MKT”, with each of
them provided an explanation and an example for the “how to” part by the system.
Each trade order made is then processed by RiSE’s engine, looking to make and complete the requested trade as fast as possible with the current active trade 
orders waiting in the system. If a trade is completed, partially completed, or couldn’t be complete at all because no correlating trade orders were found by the engine, 
a message notifying the user on the events will appear on the screen.
If a trade order couldn’t be completed, or paritally completed, it will join the system’s trade order database and await for a matching trade order to be made 
(for the current LMT and MKT trade order types. Will be updated in the future).

Option 5 prints to the screen an extensive information on the current unprocessed trade orders made for each type of stock uploaded to the system via option 1.

System Information:
There are 2 main components in “RiSE” :

1) Console.jar
This jar holds a single class “MainMenu” which stores the “main” function, as well as other sub-menus and static methods made use by main, and the MANIFEST.MF .
The MainMenu class houses 2 objects:

- A Scanner object which is used to receive info mainly from the user.
- An “Engine” object (will be explained later) to use the necessary data and perform the needed calculations, returning the desired results.

2) Engine.jar
This jar houses 4 main packages:
- Data – stores 2 sub-packages:
o data.stock – This package holds the Stock.class which is a data frame for information used in the system for the concept “stock”, as you familiar with. 
Each stock holds 3 respective lists of trade orders and completed transactions made in “RiSE”.
The second class in this package is StockList.class which is an encapsulating, self-managing class for a List data structure of Stock.class objects.
o data.tradeOrder – stores additional 2 sub packages:
▪ data.tradeOrder.order –
In this sub package you can find the abstract class Order.class which is the frame of a trade order made in the system. The other classes inside are inherited classes from Order.class, each for its designed use.
▪ data.tradeOrder.list –
A sub Package which holds classes for managing data structures of “orders” and “completed trades” , in a similar fashion to StockList.class explained earlier.

- engine :
This package holds the backbone of the program which is the Engine interface, designed to answer the overall needs of the user.
This interface is implemented by the class RiseEngineV1.class, which makes the on-site real-time calculations and designed according to the Engine interface and the project necessities. It holds a single StockList.class object for needed information and the main program memory.
- exception:
In this package you will find dedicated exceptions for this system. Mainly used by the methods within MainMenu.class, as well as the main method.
- generated:
A package made by the JAXB API. Holds classes for XML elements used in by RitzpaStockExchangeDescriptor found in XML files built in accordance to RSE-V1.xsd Schema.
