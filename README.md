# Zermelo-Java-API
An easy to use API to implement Zermelo schedules into your app. developed by Jules Hummelink.

## Getting started (in this case in Android Studio)
### Setup
1. Import the ZermeloAPI.jar into your project.
2. Make sure you add it to your project dependencies.

### Get the token
First of all, we will create the ZermeloAPI object.
```java
ZermeloAPI zermeloHelper;
```
Now set the object in onCreate:
```java
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        zermeloHelper = new ZermeloAPI();
    }
```
Now make sure, you have the school and the AuthCode from the user as Strings:
```java
String school = "testSchool";
String code = "123456789123";
```
Now start the API:
```java
zermeloHelper.start(school);
```
It is recommended to run the following commands in an AsyncTask, but for this tutorial, let's enable running network requests on the main thread (only in Android Studio. Use what is supported for your platform):
```java
StrictMode.ThreadPolicy policy = new StrictMode.ThreadPolicy.Builder().permitAll().build();
StrictMode.setThreadPolicy(policy);
```
Then finally, get the token by running the following command:
```java
String token = zermeloHelper.getToken(code);
```
Store the token and school for later use!

### Get A list with appointments
First define a start and end time in UNIX time, and you will also need the school and a token:
```java
long startTime = 1543357871;
long endTime = 154347839;
String token = "testToken";
String school = "testSchool";

ZermeloAPI zermeloHelper;
```
Now set the ZermeloAPI object in onCreate:
```java
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        zermeloHelper = new ZermeloAPI();
    }
```
Now start the API:
```java
zermeloHelper.start(school);
```
It is recommended to run the following commands in an AsyncTask, but for this tutorial, let's enable running network requests on the main thread (only in Android Studio, use what is supported for your platform):
```java
StrictMode.ThreadPolicy policy = new StrictMode.ThreadPolicy.Builder().permitAll().build();
StrictMode.setThreadPolicy(policy);
```
Now finally get a List<Appointment> by using:

```java
List<Appointment> appointments = zermeloHelper.getAppointments(startTime, endTime, token);
```

### Get data from an appointment
For example if you want the subject use:
```java
Appointment appointment = appointments.get(0);
String subject = appointment.getSubject()[0];
```
If an appointment has multiple subjects, locations, groups or teachers, it works like this:
```java
String subject1 = appointment.getSubject()[0];
String subject2 = appointment.getSubject()[1];
```

# Let me know if you have any problems:
### julescitronic.nexus@gmail.com


