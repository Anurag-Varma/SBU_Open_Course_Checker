# SBU_Open_Course_Checker

Automate the process of checking courses with Open Seats in Stony Brok University and sending the updated information messages to whatsapp if open seats are available for your selected course list. <br />

The project doen't use any vulnerabilities, it just uses your credentials in your own browser and uses selenium to navigate to 'https://stonybrook.collegescheduler.com' page and uses the API to send notifications to WhatsApp. <br />

It just automates the process instead of manual login and navigating to the end each time and making your job simpler. <br/>

It doesn't store any of your data, they are stored in your browser and in cookies which get reset after some time.


## Steps to install and make it work:
1) Install chrome browser
2) Login into solar with your details and authenticate in duo to keep it active for few days.
3) Login into WhatsApp Web in chrome browser.
4) Create an environment(I prefer with Anaconda) and install jupyter notebook if not present.
5) Install the below libraries (Present in Cell 1 of notebook)
```
# Install these libraries
!pip install selenium
!pip install pywhatkit
!pip install pyautogui
!pip install keyboard
```
6) Replace all the below thimgs with your respective details (Present in Cell 3 of notebook)
```
# Replace with the course of your choice in capital letters - string format.
#Eg: course="CSE" or course="AMS", or others, etc.
course="CSE"

# Replace with the course subject id's you want to track - list of string format. 
#Eg: interested_courses=['508','564','551', '527']
interested_courses=['508','564','551']

# Solar id (Replace with your id) - integer format
sbu_net_id=123456789

# Solar password (Replace with your password) - string format
sbu_password="YourPassword"

# Join any WhatsApp group and get the link for that group.
# Replace with the whatsApp group ending code for a whatsapp group shared link.
# Eg: if whatsapp gorup shared link is https://chat.whatsapp.com/abcdefxxxxxxxxxxxwxyz
# Then use whatsapp_group_id="abcdefxxxxxxxxxxxwxyz" - string format
whatsapp_group_id="xxxxxxxxxxxxxxxxxxxxx"
```
7) Optional, not required - [Only needed in case of whatsapp web messages are being typed in group chat but not being sent.] <br /> <br />
   Change X,Y values in pyautogui.click(1475, 645), if the message is automatically typed in whatsaspp group chat, but the text is not getting submitted. (Present in Cell 5 of notebook). <br />
   Find the approx coordinates of submit button using mouse coordinate extension - https://chrome.google.com/webstore/detail/mouse-coordinates/mfohnjojhopfcahiddmeljeholnciakl
8) Close any unnecessary chrome tabs, Now run all the 5 cells and and keep the laptop aside. <br />
    The screen should be active all the time and mouse pointer should not be in any notebook cells, click it somewhere else outside the cells and in jupyter notebook.



## Explaination Selenium:

Python Selenium does the following:
1) Logins into solar with your creds.
2) Then navigates to enrollment.
3) Then navigates to schedule builder.
4) Opens schedule builder and saves the authentication cookies to use same cookies until they expire.
5) If cookies expire, then load new cookies by repeating again from step 1.



## Explaination Api:

Api does the following:
1) Uses the auth cookies from selenium and goes to schedule builder.
2) It check for the term, course, course number, open seats, etc.
3) If open seats found in your mentioned course list, it send a whatsapp message to your group by opening whatsapp in a new tab.



## Warning:

This is for educational purpoase only, use at your own risk, I am not responsible for any damages or things.

1) Use your own credentials for login.
2) Dont run for very long time as multiple API calls may make the server slow.
3) Dont run the API too frequently by reducing the wait time.
4) Contact respective SBU admins if you want to know if this is allowed or not, I am not responsible.



## Future works:

1) Can use other data elements like flags, waitlist, etc and many other details... which are retrived from the API, but not used in this project.
2) I wrote very basic code, without any validations and not catching any excepting, this can be improved.



## References & Credit: 

https://prod.ps.stonybrook.edu/psp/csprods/?cmd=login <br />

Got inspired from the github repo: https://github.com/cougargrades/collegescheduler by Austin Jackson in which he did similar thing for UT, but I used totally different codes, libraries & concepts for SBU.
