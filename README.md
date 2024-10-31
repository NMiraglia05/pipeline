# pipeline
A data processing program I wrote in Python. The goal is to improve my ETL process.

In order to maintain a dashboard for tracking grades week-to-week, I had to export gradebooks. However, the tool used to do so did not allow combining every class together, and so I would end up with 5 excel files I'd have to combine. This simple tool uses Pandas, gspread, os.path, tkinter, and json to do its work. 

Over time, I added additional functionality so that CSV, xlsx, JSON, and google spreadsheets could all be processed and combined into one workbook/sheet. While the current format I use it in involves manual entry of files, one can imagine combining this with the webscraper I wrote or integrating it into an automated system to speed up ETL processes. 

The main function here is the "convert" function. This takes files in the format of either xlsx, csv, json, or google sheets and converts to a Pandas dataframe object. From there, the data can either be stored for further analysis via Excel, or sent to storage as a json file. 

Relatedly, the "combine" function takes two dataframes and appends them to each other as one. In its current form it can only take two inputs, however one could easily expand the function or reuse the logic elsewhere to accomplish the effect with several dataframe objects at the same time. 

The "PathCorrector" function takes file paths and fixes them so that python can read them. This was made so that my coworkers could use the program themselves without having to correct the file path by hand.

"ExcelProcessor" and "JsonProcessor" exist for similar reasons. The task I initially wrote this code for involved combigning several sheets together and saving them as an excel file. Given many of my coworkers would simply enter the desired name without the necessary file extension, I added logic to handle this automatically. JsonProcessor was as simple as converting the logic to save as json instead. Similar logic could be used anywhere else, so that a user-friendly popup handles the input, and the code corrects to the desired file type. 

While this process currently involves manual user input, it's entirely possible to integrate this into an automated process to easily perform ETL procedures to both save to databases and generate excel files.
