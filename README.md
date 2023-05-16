# Project Name
> Ticketing API
## Table of Contents
* [General Info](#general-information)
* [Technologies Used](#technologies-used)
* [Features](#features)
* [Screenshots](#screenshots)
* [Setup](#setup)
* [Usage](#usage)
* [Project Status](#project-status)
* [Room for Improvement](#room-for-improvement)
* [Acknowledgements](#acknowledgements)
* [Contact](#contact)

## General Information
- Backend of application that allow you to organise events if your role is promoter or to buy tickets if you role is member of the event.
- It will send email to you with your auto generated UUID and qr code and if you agree promoters send advertising mails to you
- I was learning how to use Spring and started to do my own project
<!-- You don't have to answer all the questions - just the ones relevant to your project. -->


## Technologies Used
- Java - version 17
- Spring Boot - 3.0.6


## Features
List the ready features here:
- JWT
- Roles
- Lombok
- Java Mail Sender
- Postgres
- Spring security

## Screenshots
![Example screenshot](./img/screenshot.png)
<!-- If you have screenshots you'd like to share, include them here. -->


## Setup
You have to create db tickets in postgres then you have to start the project
## Usage
in postman you have to register yourself by using POST on "localhost:8080/auth/register" with body pattern
{
    "username": "YOUR_NAME",
    "password":"YOUR_PASSWORD",
    "role":"ROLE"
}
in role you can choose MEMBER or PROMOTER it will return 2 JWT you shuold use the first one it is active for few days (it should be for few seconds but i set it like that just to make it simplier for testing)
you can reduce the time in a application.properties
then you can go to "localhost:8080/tickets" or "localhost:8080/events" it depends on what role you choose.If you choose PROMOTER you should POST on "localhost:8080/events/create" and youse patter:
{
            "name":"NAME OF THE EVENT",
            "place":"PLACE OF THE EVENT",
            "date":"DATE WHEN EVENT START",
            "artists":[
                {
                    "name":"NAME OF THE FIRST ARTIST"
                },{
                    "name":"NAME OF THE SECOND ARTIST"
                }
            ],
            "seats":"NUMBER OF SEATS",
            "price":"PRICE OF THE TICKET",
            "description":"SHORT DESCRIPTION OF THE EVENT",
            "promoter":"NAME OF THE COMPANY THAT CREATE EVENT"
}
on "localhost:8080/events/sendMarketing" you can POST the same patter and it will send mails to every one that agreed to the marketing in their tickets
if you choose MEMBER role you can go to "localhost:8080/tickets" try PUT with that pattern
{
    "email":"EMAIL OF THE PERSON BUYING THE TICKET",
    "name":"NAME OF THE PERSON BUYING THE TICKET",
    "lastname":"LAST NAME OF THE PERSON BUYING THE TICKET",
    "payment":"TYPE OF THE PAYMENT 'CREDIT_CARD' OR 'OTHER'",
    "agrement":"'TRUE' OR 'FALSE' IT IS AGREEMENT TO MARKETING",
    "idevent":"ID OF THE EVENT YOU CAN FIND IT IN THE DB'"
}
to buy a ticket if every thing is ok you should get an email with your ticket.
If something went wrong you can visit "localhost:8080/odzyskajbilet" and try GET with this pattern
{
    "mail": "EMAIL OF THE PERSON BUYING THE TICKET",
    "idEvent": "ID OF THE EVENT YOU BOUGHT TICKET"
}



## Project Status
Project is: _in progress_.


## Room for Improvement
TODO:
- I have to make endpoint where you could check all of the event and where you can sort them by few things like date and price
- Payment always work so i should add few options and few secure methods

Room for improvement:
- Improvement to sending email becouse it is so slow

## Contact
Created by [Dawid Brzeski](dawidsd123@gmail.com) - feel free to contact me!
