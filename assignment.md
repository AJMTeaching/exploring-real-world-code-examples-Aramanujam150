# Assignment: Exploring Real-World Code Examples
## Introduction
In our everyday lives, we interact with a myriad of software applications, often without realizing the complex code that powers them. From the moment we silence our morning alarm, to checking the weather forecast, or even making an online purchase, software is an integral part of our daily routine. As we embark on our journey to learn coding, it's essential to understand how these applications are built and function. This assignment, designed for beginners, leverages our newly acquired skills in using GitHub and other online repositories. It's an opportunity to explore and connect with the real-world applications of code.

## Objective
Your task is to delve into the world of coding by finding real-life examples of code that power the software applications you use daily. This exercise will help you understand how theoretical coding concepts are applied in practical, real-world scenarios.

## Assignment Details
Research and Exploration: Using online repositories like GitHub, search for code examples that align with the everyday software applications described in the provided prose blurbs.

Link and Line Numbers: For each example, provide the link to the code repository and specify the exact line numbers where the relevant code is located. This will help you practice navigating through code repositories and understanding code structure.

Documentation: Along with each link, write a brief description of what the code does and how it relates to the functionality of the application in the real world.

## Prose Blurbs for Exploration
- Code that specifies when an alarm clock should start making audible sounds.
https://github.com/yuriykulikov/AlarmClock <- Link to repository
https://github.com/yuriykulikov/AlarmClock/blob/develop/app/src/androidTest/java/com/better/alarm/test/InfoFragmentTest.kt <- Link to specific location
@Test
  fun prealarmOn3Days() {
    val now = Calendar.getInstance().timeInMillis
    assertThat(
            computeTexts(
                res = InstrumentationRegistry.getInstrumentation().targetContext.resources,
                alarm =
                    create(
                        Calendar.getInstance().apply {
                          timeInMillis = now
                          add(Calendar.DAY_OF_YEAR, 3)
                        },
                        true,
                    ),
                now = now,
                prealarmDuration = 30,
            ))
        .isEqualTo("3 days\n30 minutes pre-alarm")
  }
  This code tells the alarm to go off in three days. This alarm is will play a prealarm milder sound for 30 minutes in order to gradually wake up the android user it was designed to serve. This code test is on lines 50-68 in the InfoFragmentTest.kt file.

- Code for a rocket targeting system.
https://github.com/Matt4tech/Parachute-Project <- Link to repository
https://github.com/Matt4tech/Parachute-Project/blob/master/MasterDevice <- Link to code location
void loop() {
  Serial.println("Start of loop");
  //GPS
  if(canGetGPSData()){
    latitude = getLat();
    longitude = getLong();
    gpsUpdated = true;
  }else{
    gpsUpdated = false;
  }
This code is constantly running in the rocket. It is constantly recieving and sending signals out to the computers running it. This code says that if the rocket can recieve GPS data from the satellites, then it will update its latitude and longitude data and send it directly to the computers running it. This code is on lines 71-80 in the MasterDevice file.

- File compression utility algorithm.
https://github.com/flto/linux/tree/a3a80255d58d0f0d304ba877ae0313a264973a70 <- Link to repository
https://github.com/flto/linux/blob/a3a80255d58d0f0d304ba877ae0313a264973a70/Makefile#L935 <- Link to the code location.
mod_compress_cmd = true
ifdef CONFIG_MODULE_COMPRESS
  ifdef CONFIG_MODULE_COMPRESS_GZIP
    mod_compress_cmd = gzip -n -f
  endif # CONFIG_MODULE_COMPRESS_GZIP
  ifdef CONFIG_MODULE_COMPRESS_XZ
    mod_compress_cmd = xz -f
  endif # CONFIG_MODULE_COMPRESS_XZ
endif # CONFIG_MODULE_COMPRESS
export mod_compress_cmd

# Select initial ramdisk compression format, default is gzip(1).
# This shall be used by the dracut(8) tool while creating an initramfs image.
#
INITRD_COMPRESS-y                  := gzip
INITRD_COMPRESS-$(CONFIG_RD_BZIP2) := bzip2
INITRD_COMPRESS-$(CONFIG_RD_LZMA)  := lzma
INITRD_COMPRESS-$(CONFIG_RD_XZ)    := xz
INITRD_COMPRESS-$(CONFIG_RD_LZO)   := lzo
INITRD_COMPRESS-$(CONFIG_RD_LZ4)   := lz4
# do not export INITRD_COMPRESS, since we didn't actually
# choose a sane default compression above.
# export INITRD_COMPRESS := $(INITRD_COMPRESS-y)

ifdef CONFIG_MODULE_SIG_ALL
$(eval $(call config_filename,MODULE_SIG_KEY))

mod_sign_cmd = scripts/sign-file $(CONFIG_MODULE_SIG_HASH) $(MODULE_SIG_KEY_SRCPREFIX)$(CONFIG_MODULE_SIG_KEY) certs/signing_key.x509
else
mod_sign_cmd = true
endif
export mod_sign_cmd

ifdef CONFIG_STACK_VALIDATION
  has_libelf := $(call try-run,\
		echo "int main() {}" | $(HOSTCC) -xc -o /dev/null -lelf -,1,0)
  ifeq ($(has_libelf),1)
    objtool_target := tools/objtool FORCE
  else
    SKIP_STACK_VALIDATION := 1
    export SKIP_STACK_VALIDATION

This code is on lines 914-954 in the file Makefile. It compresses a file if the mod_compress command is entered. If it equals true then it is entered and the code starts runnning to compress the file into different file types. This code is used in the Linux operating system which is a system that many computer users use similar to Windows or IOS.
 
- Weather forecasting algorithm.
https://github.com/sonichy/dde-dock-weather/tree/master <- Link to repository
https://github.com/sonichy/dde-dock-weather/blob/master/forcastwidget.cpp <- Link to code location

void ForcastWidget::updateWeather()
{
    QDateTime currentDateTime = QDateTime::currentDateTime();
    QString stemp = "", stip = "", surl="";
    QString log = currentDateTime.toString("yyyy/MM/dd HH:mm:ss") + "\n";
    QNetworkAccessManager manager;
    QEventLoop loop;
    QNetworkReply *reply;

    QString city = m_settings.value("city","").toString();
    QString country = m_settings.value("country","").toString();
    if(city != "" && country != ""){
        QString icon_path = ":icon/Default/na.png";
        QString iconTheme = m_settings.value("IconTheme","").toString();
        if(iconTheme != ""){
            if(!iconTheme.startsWith("/")){
                icon_path = ":icon/" + iconTheme + "/na.png";
            }else{
                QString icon_path1 = iconTheme + "/na.png";
                QFile file(icon_path1);
                if(file.exists()){
                    icon_path = icon_path1;
                }
            }
        }
        emit weatherNow("Weather", "Temp", currentDateTime.toString("yyyy/MM/dd HH:mm:ss") + "\nGetting weather of " + city + "," + country, QPixmap(icon_path));
        QString appid = "8f3c852b69f0417fac76cd52c894ba63";
        surl = "https://api.openweathermap.org/data/2.5/forecast?q=" + city + "," + country + "&appid=" + appid;
        reply = manager.get(QNetworkRequest(QUrl(surl)));
        QObject::connect(reply, SIGNAL(finished()), &loop, SLOT(quit()));
        loop.exec();
        QByteArray BA = reply->readAll();
        log += surl + "\n";
        log += BA + "\n";
        QJsonParseError JPE;
        QJsonDocument JD = QJsonDocument::fromJson(BA, &JPE);
        if (JPE.error == QJsonParseError::NoError) {
            QString cod = JD.object().value("cod").toString();
            if(cod == "200"){
                QJsonObject JO_city = JD.object().value("city").toObject();
                QJsonObject coord = JO_city.value("coord").toObject();
                double lat = coord.value("lat").toDouble();
                double lon = coord.value("lon").toDouble();
                m_settings.setValue("lat", lat);
                m_settings.setValue("lon", lon);
                QDateTime time_sunrise = QDateTime::fromMSecsSinceEpoch(JO_city.value("sunrise").toInt()*1000L, Qt::LocalTime);
                QDateTime time_sunset = QDateTime::fromMSecsSinceEpoch(JO_city.value("sunset").toInt()*1000L, Qt::LocalTime);
                QJsonArray list = JD.object().value("list").toArray();
                int r = 0;
                for (int i=0; i<list.size(); i++) {
                    QDateTime date = QDateTime::fromMSecsSinceEpoch(list[i].toObject().value("dt").toInt()*1000L, Qt::UTC);
                    QString sdate = date.toString("MM-dd ddd");
                    QString dt_txt = list[i].toObject().value("dt_txt").toString();
                    double temp = list[i].toObject().value("main").toObject().value("temp").toDouble() - 273.15;
                    stemp = QString::number(qRound(temp)) + "°C";
                    if(m_settings.value("TemperatureUnit","°C").toString() == "°F"){
                        stemp = QString::number(qRound(temp*1.8 + 32)) + "°F";
                    }
                    QString humidity = "RH: " + QString::number(list[i].toObject().value("main").toObject().value("humidity").toInt()) + "%";
                    QString weather = list[i].toObject().value("weather").toArray().at(0).toObject().value("main").toString();
                    QString icon_name = list[i].toObject().value("weather").toArray().at(0).toObject().value("icon").toString() + ".png";
                    QString icon_path = ":icon/Default/" + icon_name;
                    QString iconTheme = m_settings.value("IconTheme","").toString();
                    if(iconTheme != ""){
                        if(!iconTheme.startsWith("/")){
                            icon_path = ":icon/" + iconTheme + "/" + icon_name;
                        }else{
                            QString icon_path1 = iconTheme + "/" + icon_name;
                            QFile file(icon_path1);
                            if(file.exists()){
                                icon_path = icon_path1;
                            }
                        }
                    }
                    QString wind = "Wind: " + QString::number(list[i].toObject().value("wind").toObject().value("speed").toDouble()) + "m/s, " + QString::number(qRound(list[i].toObject().value("wind").toObject().value("deg").toDouble())) + "°";
                    log += dt_txt + ", " + date.toString("yyyy-MM-dd HH:mm:ss ddd") + ", " + stemp + ", " + humidity + ","+ weather + ", " + icon_path + ", " + wind + "\n";
                    if(date.time() == QTime(12,0,0)){
                        if (r == 0) {
                            QPixmap pixmap(icon_path);
                            labelWImg[0]->setPixmap(pixmap.scaled(80,80,Qt::KeepAspectRatio,Qt::SmoothTransformation));
                            labelTemp[0]->setText(stemp);
                            labelDate[0]->setText(JO_city.value("name").toString());
                            labelWImg[1]->setPixmap(QPixmap(icon_path).scaled(50,50,Qt::KeepAspectRatio,Qt::SmoothTransformation));
                            labelTemp[1]->setText(weather + " " + stemp);
                            labelDate[1]->setText(sdate);
                            stip = city + ", " + country + "\n" + weather + "\n" + stemp + "\n" + humidity + "\n" + wind + "\nSunrise: " + time_sunrise.toString("hh:mm") + "\nSunset: " + time_sunset.toString("hh:mm") + "\nRefresh：" + currentDateTime.toString("HH:mm:ss");
                            emit weatherNow(weather, stemp, stip, pixmap);
                            r++;
                        } else {
                            labelWImg[r]->setPixmap(QPixmap(icon_path).scaled(50,50,Qt::KeepAspectRatio,Qt::SmoothTransformation));
                            labelTemp[r]->setText(weather + " " + stemp);
                            labelDate[r]->setText(sdate);
                        }
                        r++;
                    }
                }
            } else {
                emit weatherNow("Weather", "Temp", city + ", " + country + "\n" + cod + "\n" + JD.object().value("message").toString(), QPixmap(":icon/na.png"));
            }
        }else{
            emit weatherNow("Weather", "Temp", QString(BA), QPixmap(":icon/na.png"));
        }

        // log
        QString path = QStandardPaths::standardLocations(QStandardPaths::CacheLocation).first() + "/HTYWeather.log";
        QFile file(path);
        if (file.open(QFile::WriteOnly)) {
            file.write(log.toUtf8());
            file.close();
        }
    }
}
This code updates the weather for the Linux Forcast system. The system gathers weather data and it changes the png it shows to the user depending on if the weather is sunny, rainy, windy, etc. The code was found on lines 54-165 in the file forecastwidget.cpp. If the system cannot identify the weather or get updated data about one's location the png for no answer appears and tells the user that the app is not connected to location services or/and weather data.

- E-commerce checkout system process.
https://github.com/alvesjtiago/vue-bitcoin-checkout <- Link to repository
https://github.com/alvesjtiago/vue-bitcoin-checkout/blob/master/src/components/Checkout.vue <- Link to code location.

<template>
  <div class="hello">
    <VueQrcode class="mt4" :value="qrcodeAddress" :options="{ size: 250 }"></VueQrcode>
    <div class="f7 fw1 lh-copy">{{ address }}</div>
    <div class="mt4">{{ message }}</div>
  </div>
</template>

<script>
import VueQrcode from '@xkeshi/vue-qrcode'
const io = require('socket.io-client')

const eventToListenTo = 'tx'
const room = 'inv'

export default {
  name: 'Checkout',
  props: {
    network: String,
    address: String,
    amount: Number,
  },
  data: function() {
    return  {
      qrcodeAddress: '',
      message: ""
    }
  },
  beforeMount(){
    this.qrcodeAddress = `bitcoin:${this.address}`
    const socket = this.network == "test" ? io("https://test-insight.bitpay.com/") : io("https://insight.bitpay.com/")

    const ref = this

    socket.on('connect', function() {
      // Join the room.
      socket.emit('subscribe', room)
      ref.message = `Waiting for ${ref.amount} BTC payment...`
    })

    socket.on(eventToListenTo, function(data) {
      if (data.vout.some(e => Object.keys(e)[0] === ref.address)) {
        if (data.vout.some(e => e[ref.address] / 100000000 === ref.amount)) {
          ref.message = ""
          ref.$emit('completedPayment')
        }
      }
    })
  },
  components: {
    VueQrcode
  }
}
This code allows people to pay with Bitcoin when shopping online. The producer of a product uses the app to send consumers to a qr code that prompts them to pay with Bitcoin. This code makes sure that the producer can customize the amount of Bitcoin for the purchase and it only allows the user to have the product once it recieves the signal that the Bitcoin has been recieved. The code is on Lines 1-54 in the file Checkout.vue.

- Social media post scheduler.
https://github.com/annewoosam/social-media-minder <- This is the repository.
https://github.com/annewoosam/social-media-minder/blob/master/seed_database.py <- This is the code location.
"""Script to seed database."""

import os

import json

from datetime import datetime

import crud

import model

import server


os.system('dropdb YourFolderUnderscoredAsDatabaseNameHere')

os.system('createdb YourFolderUnderscoredAsDatabaseNameHere')

model.connect_to_db(server.app)

model.db.create_all()


# Create YourModelNameLowerCasedHere table's initial data.

with open('data/YourModelNameLowerCasedSingularHere.json') as f:

    YourModelNameLowerCasedSingularHere_data = json.loads(f.read())

YourModelNameLowerCasedSingularHere_in_db = []

for YourModelNameLowerCasedSingularHere in YourModelNameLowerCasedSingularHere_data:
    columnNamesSeparatedbyCommasUntilLastOne= (
                                   YourModelNameLowerCasedSingularHere['YourFirstColumnNameHere'],
                                   YourModelNameLowerCasedSingularHere['YourNextColumnNameHereTillLast'],
                                   YourModelNameLowerCasedSingularHere['YourLastColumnNameHere'])

    db_YourModelNameLowerCasedSingularHere = crud.create_YourModelNameLowerCasedSingularHere(
                                 YourFirstColumnNameHere,
                                 YourNextColumnNameHereTillLast,
                                 YourLastColumnNameHere)

    YourModelNameLowerCasedSingularHere_in_db.append(db_YourModelNameLowerCasedSingularHere)

This code connects a social media account's activity to the app and it also connects the current date and time to the app. By doing so it is essential for other lines of code that tell when the app needs to remind the user to post. The code is on lines 1-44 of the file seed_database.py. This app allows a person to manage their optimal social media account interactions.
- Fitness app calorie counter.
https://github.com/StormStark/Diet <- This is the repository.
https://github.com/StormStark/Diet/blob/master/app/src/main/java/com/akshat/diet/GetDetails.java <- This is the code location.

package com.akshat.diet;

import android.content.Context;
import android.content.Intent;
import android.content.SharedPreferences;
import android.os.Bundle;
import android.view.View;
import android.widget.ArrayAdapter;
import android.widget.AutoCompleteTextView;
import android.widget.Button;

import androidx.appcompat.app.AppCompatActivity;

import com.google.android.material.textfield.TextInputLayout;

public class GetDetails extends AppCompatActivity implements View.OnClickListener {

    private TextInputLayout genderTextField, nameTextField, ageTextField, weightTextField, heightTextField;
    private Button saveDetailsBtn;
    private String[] genders = {"Male", "Female", "Others"};
    private String username, fullName, password;
    public static final String MyPREFERENCES = "LoginPreference";

    SharedPreferences loginPreferences;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_get_details);

        username = getIntent().getExtras().getString("username");
        password = getIntent().getExtras().getString("password");
        fullName = getIntent().getExtras().getString("fullName");

        saveDetailsBtn = findViewById(R.id.saveDetailsBtn);
        genderTextField = findViewById(R.id.genderTextField);
        nameTextField = findViewById(R.id.nameTextField);
        ageTextField = findViewById(R.id.ageTextField);
        weightTextField = findViewById(R.id.weightTextField);
        heightTextField = findViewById(R.id.heightTextField);

        loginPreferences = getSharedPreferences(MyPREFERENCES, Context.MODE_PRIVATE);

        nameTextField.getEditText().setText(fullName);
        ArrayAdapter genderAdapter = new ArrayAdapter<String>(this,
                R.layout.list_layout, genders);

        ((AutoCompleteTextView) genderTextField.getEditText()).setAdapter(genderAdapter);

        saveDetailsBtn.setOnClickListener(this);
    }

    @Override
    public void onClick(View view) {
        switch (view.getId()) {
            case R.id.saveDetailsBtn:
                if (detailValidation()) {
                    Users user = new Users();
                    user.setFullName(fullName);
                    user.setPassword(password);
                    user.setUsername(username);
                    user.setAge(Integer.parseInt(ageTextField.getEditText().getText().toString()));
                    user.setUserWeightInKG(weightTextField.getEditText().getText().toString());
                    user.setUserHeightInCM(heightTextField.getEditText().getText().toString());
                    user.setGender(genderTextField.getEditText().getText().toString());
                    DatabaseHelper db = new DatabaseHelper(GetDetails.this);
                    db.addNewUser(user);
                    UtilityFunctions.addLoginPreference(loginPreferences, user);
                    Intent i = new Intent(GetDetails.this, NavigationActivity.class);
                    startActivity(i);
                }
                break;
        }
    }

    private boolean detailValidation() {
        if (UtilityFunctions.inputMinLengthValidation(ageTextField, 1) &&
                UtilityFunctions.inputMinLengthValidation(genderTextField, 2) &&
                UtilityFunctions.inputMinLengthValidation(weightTextField, 2) &&
                UtilityFunctions.inputMinLengthValidation(heightTextField, 2)
        ) {
            return true;
        }
        return false;
    }
}
This code is on lines 1-86 of the file GetDetails.java. In this code th calorie counter gets details about the person's health, previous exercise, age, wieght, and height. There is a password put into the app in order to make sure the right person is accessing the data at all times. This calorie counter helps users stay fit and cogniscent of the calories that they build up and burn throughout the day.
- Online voting system mechanics.
https://github.com/srajat/Online-Voting-System <- This is the repository.
https://github.com/srajat/Online-Voting-System/blob/master/Content/Voting_system_sql.sql <- This is the code location
SELECT * 
FROM INFORMATION_SCHEMA.TABLE_CONSTRAINTS 
WHERE TABLE_NAME = 'candidates'


    ALTER TABLE votes
    ALTER COLUMN voter nvarchar(15) NOT NULL
    ALTER TABLE votes ADD PRIMARY KEY (eid,candidate,voter)

    ALTER TABLE history
    DROP CONSTRAINT userId
    DROP CONSTRAINT name
    GO
    
    select votes.candidate, (select COUNT(votes.voter) as IT_votes from votes join users on votes.voter = users.id where users.branch = 'IT' group by candidate), (select COUNT(votes.voter) as ECE_votes from votes join users on votes.voter = users.id where users.branch = 'ECE' group by candidate)
    from votes
    left join votes on ();
    
    select DISTINCT vn.candidate, sq1.IT_votes,sq2.ECE_votes,sq3.BME_votes
    from votes as vn
    left outer join
    (select v.candidate,COUNT(v.voter) as IT_votes from votes as v
      join users on v.voter = users.id where users.branch = 'IT' 
      group by v.candidate)
      as sq1 on sq1.candidate = vn.candidate
     left outer join
     (select v.candidate,COUNT(v.voter) as ECE_votes from votes as v
      join users on v.voter = users.id where users.branch = 'ECE' 
      group by v.candidate)
      as sq2 on sq2.candidate = vn.candidate
       left outer join
     (select v.candidate,COUNT(v.voter) as BME_votes from votes as v
      join users on v.voter = users.id where users.branch = 'BME' 
      group by v.candidate)
      as sq3 on sq3.candidate = vn.candidate 
      where vn.eid = @eid;
      
      
      
    select DISTINCT vn.candidate, sq1.state_votes
    from votes as vn
    left outer join
    (select v.candidate,users.stateuser as state_votes from votes as v
      join users on v.voter = users.id where users.branch = 'IT' 
      group by v.candidate)
      as sq1 on sq1.candidate = vn.candidate;
      
      
      select candidate, COUNT(voter) as no_of_voters from votes 
      group by candidate order by no_of_voters DESC;
      
      select candidate , stateuser from votes,users
      
      
      select stateuser , (COUNT(stateuser)) from users
      group by stateuser;

This code makes a gui for a list of candidates for a voter to select from. The voter can only do this if they have entered in their userID and name. The code makes a table of these candidates and it is useful for promoting an interface for online voting. The code is on lines 43-98 of the file Voting_system_sql.sql.

- Automated email response system.
https://github.com/shadmanh123/Automated-Email-Response-System/tree/main <- This is the repository.
https://github.com/shadmanh123/Automated-Email-Response-System/blob/main/parta.py <- This is the code location
#Shadman Hossain 
#Oct.5, 2019
#User will enter required information and choose a subject line and depending on the subject line, program will provide an automated response

#Ask user for email
def get_user_email():
  user_email = input("Enter your Email: ")
  return(user_email)
user_email_saved = get_user_email() #Save user email information

#Ask user for message subject
def get_message_subject():
  message_subject = input("Enter your Message Subject: ")
  return(message_subject)
message_subject_saved = get_message_subject() #Save message subject information

#Ask user for message body
def get_message_body():
  message_body = input("Enter your Message Body: ")
  return(message_body)
message_body_saved = get_message_body() #Save message body information

#Check which message subject corresponds to message subject input by user
message_subject_1 = "Problem Saving File"

message_subject_2 = "I Lost My License"

message_subject_3 = "Where is My Program Installed?" 

message_subject_4 = "How Do I Open My Program?"

message_subject_5 = "How Do I Open My File In Microsoft Word?"

message_subject_6 = "Do You Offer Refunds?"

if message_subject_saved == "Problem Saving File" or message_subject_saved == "1" or message_subject_saved.lower() == message_subject_1.lower():
  message_subject_one = "    Thank you for contacting our company. Saving a file is done by pressing CTRL-S (Windows) or CMD-S (Mac)."
  message_subject_saved = message_subject_one

elif message_subject_saved == "I Lost My License" or message_subject_saved == "2" or message_subject_saved.lower() == message_subject_2.lower():
  message_subject_two = "    Thank you for contacting our company. You will be contacted via email to verify your license request."
  message_subject_saved = message_subject_two

elif message_subject_saved == "Where is My Program Installed?" or message_subject_saved == "3" or message_subject_saved == "How Do I Open My Program?" or message_subject_saved == "4" or message_subject_saved.lower() == message_subject_3.lower() or message_subject_saved.lower() == message_subject_4.lower() :
  message_subject_three_or_four = "    Thank you for contacting our company. The application is located in the folder: \n                     My Computer > Program Files \n                   Double click on the application to launch and run it."
  message_subject_saved = message_subject_three_or_four

elif message_subject_saved == "How Do I Open My File In Microsoft Word?" or message_subject_saved == "5" or message_subject_saved.lower() == message_subject_5.lower():
  message_subject_five = "    Thank you for contacting our company. First export the file in .doc format in our application. Then open the .doc file in Microsoft Word."
  message_subject_saved = message_subject_five

elif message_subject_saved == "Do You Offer Refunds?" or message_subject_saved == "6" or message_subject_saved.lower() == message_subject_6.lower():
  message_subject_six = "    Thank you for contacting our company. Sorry, we do not offer refunds."
  message_subject_saved = message_subject_six

#Look for key phrases in message body to determine response if no message subject is given

key_phrases1 = ["can't save file","saving","save"]

key_phrases2 = ["license", "lost license"]

key_phrases3_or_4 = ["can’t find my program","cannot find my program","can’t find the program","where is the program","can’t open my program","cannot open my program","can't open the program"]

key_phrases5 = ["open in word","open in ms word"]

key_phrases6 = ["refund","have a refund","get a refund","want a refund", "REFUND"]

if message_subject_saved == "":
  for phrases in key_phrases1:
    if phrases in message_body_saved:
      message_subject_one = "    Thank you for contacting our company. Saving a file ic)."
      message_subject_saved = message_subject_one

  for phrases in key_phrases2:
    if phrases in message_body_saved:
      message_subject_two = "    Thank you for contacting our company. You will be contacted via email to verify your license request."
      message_subject_saved = message_subject_two

  for phrases in key_phrases3_or_4:
    if phrases in message_body_saved:
      message_subject_three_or_four = "    Thank you for contacting our company. The application is located in the folder: \n                     My Computer > Program Files \n                   Double click on the application to launch and run it."
      message_subject_saved = message_subject_three_or_four
    

  for phrases in key_phrases5:
    if phrases in message_body_saved:
      message_subject_five = "    Thank you for contacting our company. First export the file in .doc format in our application. Then open the .doc file in Microsoft Word."
      message_subject_saved = message_subject_five

  for phrases in key_phrases6:
    if phrases in message_body_saved:
      message_subject_six = "    Thank you for contacting our company. Sorry, we do not offer refunds."
      message_subject_saved = message_subject_six


#print blank line
print()

#Greet user
print("Dear", user_email_saved+",")

#Display automated message appropriate to Subject line
print(message_subject_saved)

#Thank user
print("Thank you,")

#Display company name
print("Company Customer Service")

#End response

This code is written to find common phrases and subject lines in an email to a busy secretary and it sends an automatic response unique for each of those subject lines. Most likely this email specificity is explained to the customer when they need help with some information before they are refered to a real person. This system prompts the user to enter their email and it allows for major companies to save time and effort when doing customer service. The code is in lines 1-111 and it is located on the file parta.py.

}

Three Tools in My Life

- How my computer autocorrects my spelling
https://github.com/filyp/autocorrect/tree/master <- This is the repository.
https://github.com/filyp/autocorrect/blob/master/autocorrect/typos.py <- This is the code location.
# Python 3 Spelling Corrector
#
# Copyright 2014 Jonas McCallum.
# Updated for Python 3, based on Peter Norvig's
# 2007 version: http://norvig.com/spell-correct.html
"""
Word based methods and functions

Author: Jonas McCallum
https://github.com/foobarmus/autocorrect

Optimized by: Filip Sondej
https://github.com/fifimajster/autocorrect/

"""

from itertools import chain

from autocorrect.constants import alphabets


class Word:
    """container for word-based methods"""

    __slots__ = ["slices", "word", "alphabet", "only_replacements"]  # optimization

    def __init__(self, word, lang="en", only_replacements=False):
        """
        Generate slices to assist with typo
        definitions.

        'the' => (('', 'the'), ('t', 'he'),
                  ('th', 'e'), ('the', ''))

        """
        slice_range = range(len(word) + 1)
        self.slices = tuple((word[:i], word[i:]) for i in slice_range)
        self.word = word
        self.alphabet = alphabets[lang]
        self.only_replacements = only_replacements

    def _deletes(self):
        """th"""
        for a, b in self.slices[:-1]:
            yield "".join((a, b[1:]))

    def _transposes(self):
        """teh"""
        for a, b in self.slices[:-2]:
            yield "".join((a, b[1], b[0], b[2:]))

    def _replaces(self):
        """tge"""
        for a, b in self.slices[:-1]:
            for c in self.alphabet:
                yield "".join((a, c, b[1:]))

    def _inserts(self):
        """thwe"""
        for a, b in self.slices:
            for c in self.alphabet:
                yield "".join((a, c, b))

    def typos(self):
        """letter combinations one typo away from word"""
        if self.only_replacements:
            return chain(self._replaces())
        else:
            return chain(
                self._deletes(), self._transposes(), self._replaces(), self._inserts()
            )

    def double_typos(self):
        """letter combinations two typos away from word"""
        return chain.from_iterable(
            Word(e1, only_replacements=self.only_replacements).typos()
            for e1 in self.typos()
        )

This code is found in lines 1-78 on the file typos.py. The code defines certain kinds of typos and connects with a libraray interface to crossreference data and determine if an error was made that needs to be autocorrected. The code helps editors type at much faster speeds and get their thoughts down in less time.  

- How macbook batteries reduce overcharging
https://github.com/zackelia/bclm <- This is the repository.
https://github.com/zackelia/bclm/blob/main/Sources/bclm/main.swift <- This is the code location.
 struct Write: ParsableCommand {
        static let configuration = CommandConfiguration(
            abstract: "Writes a BCLM value.")

#if arch(x86_64)
        @Argument(help: "The value to set (50-100)")
        var value: Int
#else
        @Argument(help: "The value to set (80 or 100)")
        var value: Int
#endif

        func validate() throws {
            guard getuid() == 0 else {
                throw ValidationError("Must run as root.")
            }

#if arch(x86_64)
            guard value >= 50 && value <= 100 else {
                throw ValidationError("Value must be between 50 and 100.")
            }
#else
            guard value == 80 || value == 100 else {
                throw ValidationError("Value must be either 80 or 100.")
            }
#endif
        }

        func run() {
            do {
                try SMCKit.open()
            } catch {
                print(error)
            }
This code helps macbook batteries reduce overchargin by setting a max limit for certain amounts of charge flow. If the charge is between 50 and 100 the computer will allow more charge into it that if the charge is between 80 and 100. It will exponentially decrease to protect the battery health of the computer. The gaurd value can be set to 80 or 100 to determine if the computer should protect it's battery and reduce the incoming charge at 80% or at 100%. This code is on lines 41-74 in the file main.swift. 

- How does email filter spam?
https://github.com/rspamd/rspamd <- This is the repository
https://github.com/rspamd/rspamd/blob/master/doc/rspamc.1 <- This is the code location.
On exit \f[C]rspamc\f[] returns \f[C]0\f[] if operation was successful
and an error code otherwise.
.SH EXAMPLES
.PP
Check stdin:
.IP
.nf
\f[C]
rspamc\ <\ some_file
\f[]
.fi
.PP
Check files:
.IP
.nf
\f[C]
rspamc\ symbols\ file1\ file2\ file3
\f[]
.fi
.PP
Learn files:
.IP
.nf
\f[C]
rspamc\ \-P\ pass\ learn_spam\ file1\ file2\ file3
\f[]
.fi
.PP
Add fuzzy hash to set 2:
.IP
.nf
\f[C]
rspamc\ \-P\ pass\ \-f\ 2\ \-w\ 10\ fuzzy_add\ file1\ file2
\f[]
.fi
.PP
Delete fuzzy hash from other server:
.IP
.nf
\f[C]
rspamc\ \-P\ pass\ \-h\ hostname:11334\ \-f\ 2\ fuzzy_del\ file1\ file2
\f[]
.fi
.PP

This code allows the email client to check for spam messages and learn what constitutes a spam message over time. This code adds fuzzy hashes to messages it has deemed as spam and then a different part of the code uses that hash to put the fuzzy hash marked messages into the spam folder. This code is on lines 229-272 in the file rspamc.1.
## Submission Format

Document Title: "Exploring Code in Daily Life"
Content Structure: For each of the nine blurbs, include a heading with the blurb title, followed by your findings (link and line numbers) and a brief description. Also, do the same for 3 kinds of tools you use every day (for example: how the email app knows there are new messages, how my calendar adds new items, how my video game authenticates my user/password)
Length: No more than two paragraphs per blurb.
Evaluation Criteria
Accuracy: Correctly identifying relevant sections of code.
Clarity: Clear and concise descriptions of how the code functions.
Research Skills: Ability to effectively use online resources like GitHub.
