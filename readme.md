# OCR - Bot
A Simple Discord Bot for OCR which is enabled by [pytesseract](https://pypi.org/project/pytesseract/) library. Deployable on Heroku (steps to deploy below).

### If you just want to add an OCR bot on your server , use this [OCR-Bot on top.gg](https://top.gg/bot/805507110363201547).

As a personal preference, this bot requires no command to do OCR. So add it to a separate channel and make sure other channels are not visible to it.


# Instructions:
 - Clone the repo
 - Install all the requirements
     ```sh
    pip install -r requirements.txt
    ```
- These requirements include "opencv-headless", if you are trying it on a machine which doesn't support it, install the [normal OpenCV](https://pypi.org/project/opencv-python/) library.

- Install tesserct-ocr using this command:
    - On Ubuntu
      ```
      sudo apt-get install tesseract-ocr
      ```
    - On Mac
      ```
      brew install tesseract
      ```
    - On Windows, download installer from [here](https://github.com/UB-Mannheim/tesseract/wiki)
 
- ### Don't forget to add your "BOT_TOKEN" in the "bot.py" file.

- Run the python bot using the command: 
    ```sh
    python bot.py
   ```
    or
    ```sh
    python3 bot.py
    ```
 <br />
 <br />

# Deploying on Heroku (as on Feb-2021)
- Uncomment the line as shown below before deploying to Heroku:

<img src="assets/uncomment.png" alt="" width="90%" height="70%"/>

- Create an account on [Heroku](https://www.heroku.com/) <br />

- Click on "New" -> "Create new App" <br />

<img src="assets/new-app.png" alt="" width="90%" height="70%"/>

- When you click on "Create App", you'll be greeted with this section : <br />

<img src="assets/first-deploy.png" alt="" width="90%" height="70%"/>

- Jump to "Settings" where you'll scroll down to see "Config Vars" & "Buildpacks": <br />

<img src="assets/buildpack.png" alt="" width="90%" height="70%"/>

- Add "Python Buildpack" and the below mentioned buildpack : 

     ```sh
    https://github.com/heroku/heroku-buildpack-apt
    ```
    <br />

    <img src="assets/python-bp.png" alt="" width="70%" height="55%"/>

    <img src="assets/custom-bp.png" alt="" width="70%" height="55%"/>

    <img src="assets/final-bp.png" alt="" width="70%" height="55%"/>

    <br />

- After adding both buildpacks, click on "Reveal Config Vars" : <br />

    <img src="assets/config-vars.png" alt="" width="90%" height="90%"/>

- Add the below mentioned "Key = Value" Pair :

     ```sh
    TESSDATA_PREFIX = ./.apt/usr/share/tesseract-ocr/4.00/tessdata
    ```
    <br />

    <img src="assets/fin-config-vars.png" alt="" width="90%" height="90%"/>


- After adding both Buildpacks and Config variables,  we're now ready to deploy.

- Follow the Steps given in "Deploy" section of your Heroku app. <br />

- ## But,  First we have to change the Heroku stack to "heroku-18"

    - Changing it to "heroku-18" made it work for me.

    - Type in the first three commands in your bot directory (assuming you have [heroku CLI](https://devcenter.heroku.com/articles/heroku-cli) installed) : 

    ```sh
    heroku login
    ```

    ```sh
    git init
    ```

    ```sh
    heroku git:remote -a "Your-app-name"
    ```


    <img src="assets/first-two-cmd.png" alt="" width="70%" height="70%"/> 

     <br /> 

    - Before the "git add ." command, use this command to change the stack to "heroku-18"

         ```sh
         heroku stack:set heroku-18
        ```

    <img src="assets/stack-18.png" alt="" width="70%" height="70%"/>
        <br />

    - Then you can proceed with the commands : 

    ```sh
    git add .
    ```

    ```sh
    git commit -am "make it better"
    ```

    ```sh
    git push heroku master
    ```

    <br />

    <img src="assets/done-dep.png" alt="" width="70%" height="70%"/>
    
- It'll take time to push the bot to heroku. Be patient.

- After the build has succeeded, you can go and start your bot by going into "resources" tab and turning the "bot.py" worker ON.

    - Click on the edit icon and turn the bot ON.

    <img src="assets/bot-on.png" alt="" width="90%" height="90%"/>


### That's it, your bot is now live. (If you didn't forget to add your "BOT_TOKEN" in the bot.py file.)
    



