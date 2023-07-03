
# Doctor Appointment Android App Using Firebase 

The Doctor Appointment Android App is a comprehensive application designed to streamline the appointment management process for a clinic. The app utilizes Firebase, a powerful mobile and web development platform, to store and retrieve data securely. 

The app consists of two main user roles: doctors and patients. Doctors have access to features that allow them to manage appointments and issue prescriptions, while patients can book appointments, view prescriptions, and download them for future reference. 

Key features of the app include:

**1. Doctor Dashboard:** Doctors have a personalized dashboard that displays their upcoming appointments, patient details, and prescription requests. They can easily manage and reschedule appointments, view patient medical histories, and update patient information.

**2. Appointment Booking:** Patients can register and log in to the app to book appointments with their preferred doctors. They can view the available time slots, select a convenient appointment slot, and receive confirmation through a notification.

**3. Prescription Management:** Doctors can issue prescriptions digitally through the app. They can create personalized prescriptions, add medication details, dosage instructions, and any additional notes. Patients can securely access their prescriptions within the app, view the details, and download them for offline access.

**4. Notifications:** The app sends push notifications to patients for various actions, such as appointment confirmations, reminders, and prescription availability. This ensures that patients stay updated and informed about their appointments and prescriptions.

**5. Data Security:** The app ensures data security and confidentiality by utilizing Firebase's authentication and database services. Patient data and medical information are encrypted and securely stored, complying with privacy regulations.

The Doctor Appointment Android App provides a user-friendly and efficient solution for doctors and patients to manage appointments and prescriptions seamlessly. It enhances the clinic's operational efficiency and improves the overall patient experience by reducing waiting times and facilitating easy access to prescriptions and appointment details.


## Dependency 
Here is the table listing the dependency versions mentioned in our code:

| Dependency                                             | Version    |
|--------------------------------------------------------|------------|
| androidx.appcompat:appcompat                           | 1.6.1      |
| com.google.android.material:material                   | 1.9.0      |
| androidx.constraintlayout:constraintlayout             | 2.1.4      |
| com.google.firebase:firebase-auth-ktx                  | 22.0.0     |
| com.google.firebase:firebase-database-ktx              | 20.2.1     |
| com.google.firebase:firebase-storage-ktx               | 20.2.0     |
| com.google.firebase:firebase-messaging-ktx             | 23.1.2     |
| androidx.navigation:navigation-fragment                | 2.5.3      |
| androidx.navigation:navigation-ui                      | 2.5.3      |
| com.google.android.gms:play-services-maps              | 18.1.0     |
| junit:junit                                            | 4.13.2     |
| androidx.test.ext:junit                                | 1.1.5      |
| androidx.test.espresso:espresso-core                   | 3.5.1      |
| com.google.android.gms:play-services-auth              | 20.5.0     |
| com.github.bumptech.glide:glide                         | 4.15.1     |
| com.karumi:dexter                                      | 6.0.2      |
| com.github.denzcoskun:ImageSlideshow                   | 0.1.2      |
| androidx.recyclerview:recyclerview                     | 1.3.0      |
| com.squareup.retrofit2:retrofit                        | 2.1.0      |
| com.squareup.retrofit2:converter-gson                  | 2.1.0      |
| de.hdodenhof:circleimageview                           | 3.1.0      |
| com.itextpdf:itextpdf                                  | 5.0.6      |
| com.google.firebase:firebase-auth                      | 21.0.3     |
| com.google.firebase:firebase-database                  | 20.0.4     |
| com.google.firebase:firebase-storage                   | 20.0.1     |
| com.google.firebase:firebase-messaging                 | 23.0.3     |
| com.firebaseui:firebase-ui-database                    | 8.0.2      |
| com.google.android.gms:play-services-maps              | 17.0.0     |
| com.google.android.gms:play-services-location          | 18.0.0     |
| com.google.maps.android:android-maps-utils             | 2.2.0      |



---


## Functional Components 
### Doctor 
**1. DoctorLogin Activity**

The `DoctorLoginActivity` is responsible for handling the login functionality for doctors in the Doctor Appointment Android App. This activity allows doctors to log in using their email and password credentials.

The main components and features of the `DoctorLoginActivity` are as follows:

1. **UI Components**: The activity layout contains two `EditText` views for entering the email and password, respectively. These views are initialized as `email` and `password` variables.

2. **Firebase Authentication**: The activity utilizes Firebase Authentication to handle the login process. The `FirebaseAuth` instance is created and stored in the `firebaseAuth` variable.

3. **Progress Dialog**: A `ProgressDialog` is displayed to the user during the login process to indicate that the authentication is in progress. It is initialized as `progressDialog`.

4. **OnCreate() Method**: In the `onCreate()` method, the activity layout is set, the action bar is hidden, and the window flags are adjusted to display the activity in fullscreen mode. Additionally, the UI components are initialized, and the `FirebaseAuth` instance is obtained.

5. **User Check**: If a user is already logged in, their UID is checked against a specific value ("##################" in this case). If the UID matches, the user is redirected to the `DoctorDashboard` activity.

6. **Doctor Login**: When the user clicks the "Login" button, the `doctorLogin()` method is triggered. The method retrieves the email and password entered by the user and performs input validation. If the inputs are valid, the `doctorLoginCheck()` method is called to authenticate the doctor's credentials.

7. **Authentication Listener**: The `signInWithEmailAndPassword()` method is used to sign in the doctor with the provided email and password. An `OnCompleteListener` is added to handle the authentication task's completion. If the login is successful, the `updateUI()` method is called, and the doctor is redirected to the `DoctorDashboard` activity. Otherwise, an error message is displayed.

8. **Update UI**: The `updateUI()` method checks if the authenticated user is not null and has a specific UID value ("n6KwVzBPM8aKN2tWTb0h6aDC5EG3" in this case). If the conditions are met, a success message is displayed, and the doctor is redirected to the `DoctorDashboard` activity.

9. **Lifecycle Methods**: The `onStart()` method is empty, and the `onBackPressed()` method is overridden to handle the back button press by finishing the activity.



**2. DoctorDashboard Activity**

The `DoctorDashboard` activity is responsible for displaying the dashboard interface for doctors in the Doctor Appointment Android App. This activity provides various features and options for doctors to manage their appointments and interact with patients.

The main components and features of the `DoctorDashboard` activity are as follows:

1. **UI Components**: The activity layout contains several UI components such as `CircleImageView` for displaying the doctor's profile image, `TextView` for displaying the doctor's name and degree, and `CardView` elements for different functionalities.

2. **Firebase Authentication**: The activity checks the user's authentication status using Firebase Authentication. If the user is not authenticated or does not have the specified UID ("################"), the app finishes and returns to the login screen.

3. **Profile Data Retrieval**: The activity retrieves the doctor's profile data from the Firebase Realtime Database. The `DoctorProfile` reference is used to fetch the relevant data fields such as doctor name, degree, experience, email, contact, address, and profile image URL. The retrieved data is displayed in the corresponding UI components.

4. **CardView Listeners**: The activity sets click listeners on the various `CardView` elements to handle different actions:
   - **Book Appointment**: When clicked, this card view hides the current layout and displays a nested scroll view with the `NewAppoinment` fragment.
   - **Today's Appointment**: When clicked, this card view starts the `TodaysAppoinment` activity to display appointments scheduled for the current day.
   - **Prescription History**: When clicked, this card view starts the `PrescriptionHistoryData` activity to display the history of prescribed medications.
   - **Send Notification**: When clicked, this card view starts the `SendNotification` activity to send notifications to users.
   - **User Profile**: When clicked, this card view starts the `UserProfileForDoctorNotify` activity to view and send notifications to a specific user.
   - **All Appointment Data**: When clicked, this card view starts the `AllUserAppoinmentDataInTable` activity to display all appointment data in a table format.

5. **Edit Profile**: When the "Edit Profile" button is clicked, the `UpdateDoctorProfile` activity is started to allow doctors to edit their profile data.

6. **Logout**: When the "Logout" button is clicked, the user is signed out from Firebase Authentication, and the app returns to the `DoctorLoginActivity`.

7. **Back Button Behavior**: The activity overrides the `onBackPressed()` method to handle the back button press. If there are fragments in the back stack, the top fragment is popped and the `DoctorDashboard` activity is started again. Otherwise, a confirmation dialog is shown to ask the user to confirm the exit from the app.

8. **Lifecycle Methods**: The `onStart()` method is overridden to hide the action bar and set the status bar color.

9. **Fragment Replacing**: The `replaceFragments()` method is used to replace fragments within the activity's layout. It uses the `FragmentManager` and `FragmentTransaction` to perform the fragment replacement.




**3. DoctorProfile_Fragment**

The `DoctorProfile_Fragment` class represents a fragment in the Doctor Appointment Android App responsible for displaying a doctor's profile information. Here's a breakdown of the code:

- The fragment extends the `Fragment` class and serves as a UI component that can be added to an activity.

- The fragment contains various UI components such as `TextView` and `CircleImageView` for displaying the doctor's profile information.

- The `newInstance` factory method is provided to create a new instance of the fragment with optional parameters.

- The `onCreate` method is overridden to retrieve any arguments passed to the fragment during creation.

- In the `onViewCreated` method, the fragment initializes the UI components by finding their respective views using `findViewById`.

- The `profileDATA` method is responsible for retrieving the doctor's profile data from the Firebase Realtime Database. It sets up a `ValueEventListener` on the specified database reference and listens for changes in the data.

- When the data changes, the `onDataChange` method is called, and the retrieved profile data is populated into the corresponding UI components. The `Glide` library is used to load the doctor's profile image from the provided URL.

- If an error occurs during data retrieval or when cancelling the event, error messages are displayed using `Toast`.

- The `onCreateView` method is overridden to inflate the fragment's layout from the specified XML file (`fragment_doctor_profile_`).

Overall, the `DoctorProfile_Fragment` displays a doctor's profile information by retrieving the data from the Firebase Realtime Database and populating the UI components accordingly.




**4. TodaysAppoinment**

The `TodaysAppoinment` class is an activity in the Doctor Appointment Android App that displays the appointments scheduled for the current day. Here's a breakdown of the code:

- The activity extends the `AppCompatActivity` class and implements the `SelectListner` interface, which defines a callback method for when an item is clicked in the appointment list.

- Various imports are included to support the functionality of the activity.

- The activity sets the title and background color of the action bar and changes the status bar color.

- The `currentdate` variable is initialized with the current date using the `SimpleDateFormat` class.

- The `onCreate` method sets up the search functionality by retrieving the search view from the layout and attaching a listener to it. The listener filters the appointment list based on the search query. Additionally, the `getTodaysActiveAppoinment` method is called to fetch the appointments for the current date.

- The `getTodaysActiveAppoinment` method retrieves the appointments for the current date from the Firebase Realtime Database. It sets up a query to find appointments where the "date" field matches the current date. The method then initializes the RecyclerView and sets up the adapter and layout manager for displaying the appointment list. A `ValueEventListener` is added to the query to listen for changes in the data. When the data changes, the listener populates the appointment list and notifies the adapter of the data change.

- The `onBackPressed` method is overridden to finish the activity when the back button is pressed.

- The `onItemClicked` method is implemented from the `SelectListner` interface. It is called when an appointment item is clicked in the list. The method retrieves the selected appointment's information and starts the `PrescriptionIssuedByDoctor` activity, passing the relevant data as extras in the intent.

Overall, the `TodaysAppoinment` activity displays the appointments scheduled for the current day and allows the user to search for specific appointments. It also provides the functionality to view detailed information about a selected appointment and navigate to the `PrescriptionIssuedByDoctor` activity.




**5. PrescriptionIssuedByDoctor**

The `PrescriptionIssuedByDoctor` class is an activity in the Doctor Appointment Android App that allows a doctor to issue a prescription for a patient. Here's a breakdown of the code:

- The activity extends the `AppCompatActivity` class and initializes various UI elements and variables.

- The necessary imports are included to support the functionality of the activity.

- The activity retrieves the data passed from the previous activity using `getIntent()` and `getStringExtra()` methods. The data includes the user ID, patient name, appointment ID, age, mobile number, health problem, date, time, gender, and address.

- The activity sets the title and background color of the action bar and changes the status bar color.

- The layout elements are initialized and populated with the retrieved data.

- The `saveprescription` button's `OnClickListener` is set to handle the prescription saving functionality. When the button is clicked, the method retrieves the values entered in the form and performs input validation. If all the required fields are filled, the `savedPrescriptionData` method is called to save the prescription data.

- The `savedPrescriptionData` method creates a `prescriptionGeneratorList` object with the prescription details. It then initializes the Firebase Realtime Database and saves the prescription data under the "prescriptionData" node with the appointment ID as the key. If the saving operation is successful, an alert dialog is displayed, and the activity navigates back to the `TodaysAppoinment` activity. If the saving operation fails, a different alert dialog is displayed.

Overall, the `PrescriptionIssuedByDoctor` activity allows the doctor to enter prescription details and save them in the Firebase Realtime Database.

**6. PrescriptionHistoryData**

The `PrescriptionHistoryData` class is an activity in the Doctor Appointment Android App that displays the prescription history. Here's a breakdown of the code:

- The activity extends the `AppCompatActivity` class and implements the `SelectListner2` interface.

- The necessary imports are included to support the functionality of the activity.

- The activity sets the title and background color of the action bar and changes the status bar color.

- The `onCreate` method initializes the RecyclerView, sets up the search functionality using a SearchView, and calls the `getHistoryData` method.

- The `getHistoryData` method retrieves the prescription history data from the Firebase Realtime Database. It creates a query to order the data by the "issueddatetime" field. It initializes the RecyclerView, ArrayList, and prescriptionAdapter. It attaches a ValueEventListener to the query to fetch the data from the database and populates the ArrayList with the retrieved prescription data. Finally, it notifies the adapter that the data has changed.

- The `onItemClicked` method is implemented from the `SelectListner2` interface. When an item in the RecyclerView is clicked, this method is called. It creates an intent to open the `Prescription_Generator_PDF` activity and passes the necessary data as extras. The intent is then started.

Overall, the `PrescriptionHistoryData` activity retrieves the prescription history data from the Firebase Realtime Database and displays it in a RecyclerView. It also provides search functionality and allows the user to view the details of a specific prescription by clicking on it.


**7. Prescription_Generator_PDF**

The `Prescription_Generator_PDF` class is an activity in the Doctor Appointment Android App that generates and saves a prescription as a PDF file. Here's a breakdown of the code:

- The activity extends the `AppCompatActivity` class.

- The necessary imports are included to support the functionality of the activity.

- The activity sets the title and background color of the action bar and changes the status bar color.

- The `onCreate` method retrieves the prescription data from the intent extras passed from the `PrescriptionHistoryData` activity. It initializes TextViews to display the patient information and medication details. It also sets a click listener on the download button.

- The `checkPermission` method checks if the app has the necessary write external storage permission.

- The `requestPermission` method requests the write external storage permission from the user.

- The `onRequestPermissionsResult` method is called when the user responds to the permission request. If the permission is granted, the `DownloadPrescription` method is called. Otherwise, a toast message is displayed.

- The `onBackPressed` method is overridden to finish the activity when the back button is pressed.

- The `DownloadPrescription` method is called when the user clicks the download button. It captures the screenshot of the card view containing the prescription using the drawing cache. It then saves the captured image to a file and calls the `imageToPDF` method.

- The `imageToPDF` method converts the captured image to a PDF file. It creates a new document, sets the output file path, and adds the image to the document. Finally, it closes the document and displays a toast message indicating that the PDF has been saved.

Overall, the `Prescription_Generator_PDF` activity allows the user to generate and save a prescription as a PDF file. The prescription data is displayed on the screen, and when the user clicks the download button, the prescription is captured as an image and converted to a PDF file.


**8. UpdateDoctorProfile**


The provided code is an Android application code written in Java. It appears to be an activity class called "UpdateDoctorProfile" that allows doctors to update their profile information and profile image. Here is a breakdown of the code:

1. The necessary import statements are included.

2. The activity extends the AppCompatActivity class and overrides the onCreate() method.

3. The layout elements such as EditText, ImageView, and Button are declared and initialized.

4. ProgressDialog objects are created to show progress during profile data updates and image uploads.

5. The profileDATA() method retrieves the existing profile data from the Firebase Realtime Database and sets it to the corresponding EditText and ImageView.

6. The uploadDcImg ImageView has a click listener that calls the updateProfileImage() method to allow the user to select and upload a new profile image.

7. The updateProfileData Button has a click listener that retrieves the input data from the EditText fields and checks for empty fields. If all fields are filled, the updateDoctorData() method is called to update the profile data in the Firebase Realtime Database.

8. The profileImg ImageView also has a click listener that opens the gallery to select a new profile image. The selected image is then displayed in the ImageView.

9. The onActivityResult() method handles the result of selecting an image from the gallery.

10. The updateProfileImage() method uploads the selected image to Firebase Storage and updates the profile image URL in the Firebase Realtime Database.

11. The updateDoctorData() method updates the profile data in the Firebase Realtime Database.

12. The onStart() method hides the action bar and sets the activity to fullscreen.

Please note that this code assumes the presence of the necessary XML layout file and Firebase configuration in the project.

**9. SendNotification**

 It includes an activity class called "SendNotification" that allows sending push notifications to either all devices or a specific device.

The activity layout contains EditText fields for entering the notification title, message, and user token. The user token is used to send a notification to a specific device. There is also a button for sending the notification to all devices and another button for sending the notification to a specific device.

The code initializes the EditText fields and retrieves the user token and username from the intent extras. It sets the title of the activity and customizes the action bar's background color and status bar color.

The code uses Firebase Messaging to subscribe to a topic called "TOPIC" and sends notifications to devices subscribed to this topic.

The sendToAll method is called when the "Send to All" button is clicked. It checks if the title and message fields are empty and displays a toast message if they are. If the fields are not empty, it creates a PushNotification object with the title, message, and the "TOPIC" topic. Then it calls the sendNotification method to send the notification.

The sendNotification method makes a network request using the ApiUtilities class to send the notification. It shows a toast message if the notification is sent successfully or displays an error message if the request fails.

The onBackPressed method is overridden to finish the activity when the back button is pressed.

The sendToOne method is called when the "Send to One" button is clicked. It performs similar checks for the title, message, and user token fields. If they are not empty, it creates a NotificationData object with the title and message, and a PushNotification object with the data and the user token. It then makes a network request to send the notification and shows a toast message with the result.

Overall, the code provides functionality to send push notifications to either all devices or a specific device using Firebase Messaging and a REST API.

**10. UserProfileForDoctorNotify**


It includes an activity class called "UserProfileForDoctorNotify" that displays a list of user profiles and allows selecting a profile to send a notification to.

The activity layout contains a RecyclerView to display the user profiles.

The code initializes the RecyclerView, sets the title of the activity, and customizes the action bar's background color and status bar color.

The getAllProfileData method retrieves user profiles from the Firebase Realtime Database. It creates a query to get the "userProfile" data from the database and orders it by the "username" field. It sets up the RecyclerView with a custom adapter (profileAdapterForGettingData) and an ArrayList (pflist) to store the retrieved profiles. The adapter is responsible for binding the profile data to the RecyclerView. It also implements the SelectListner3 interface to handle item clicks in the RecyclerView.

Inside the onDataChange method, the code iterates through the retrieved data snapshots and creates profiledataholder objects from the snapshot values. It adds these objects to the pflist ArrayList and notifies the adapter of the data change.

If there is an error during the database query, the onCancelled method is called, and a toast message is displayed.

The onItemClicked method is implemented from the SelectListner3 interface. It is called when an item in the RecyclerView is clicked. It creates an intent to start the "SendNotification" activity and passes the selected user's token and username as intent extras.

The onBackPressed method is overridden to finish the activity when the back button is pressed.

Overall, the code retrieves user profiles from the Firebase Realtime Database and displays them in a RecyclerView. It allows selecting a profile to send a notification by starting the "SendNotification" activity with the selected user's token and username.


## API Reference For Send Notification
### sendNotification

Sends a push notification.

```java
@Headers({"Authorization: key="+SERVER_KEY,"Content-Type:"+CONTENT_TYPE})
@POST("fcm/send")
Call<PushNotification> sendNotification(@Body PushNotification pushNotification)
```

| Parameter          | Type                          | Description                              |
| :----------------- | :---------------------------- | :--------------------------------------- |
| `pushNotification` | `PushNotification` (request body) | **Required**. Push notification payload. |

The `PushNotification` object should contain the necessary data for sending the notification, such as the recipient's token, title, body, and any other relevant information.

Make sure to replace `SERVER_KEY` and `CONTENT_TYPE` with your actual server key and content type.

Feel free to modify the example or add additional details as needed for your API reference.
## Optimizations

- Optimized UI for enhanced user experience.
- Implemented Firebase Cloud Messaging (FCM) for real-time notifications.
- Added functionality to save prescriptions on the device.
- Patients can view their prescription history without the need to download.
- Prescription history allows patients to easily access and view their prescriptions.
## Screenshots

| Screenshot 1 | Screenshot 2 | Screenshot 3 |
|--------------|--------------|--------------|
| ![App Screenshot 1](https://firebasestorage.googleapis.com/v0/b/filehostingvrn.appspot.com/o/files%2F3%2F7%2F2023%2C%209%3A48%3A15%20pm_Screenshot_20230703-212027.png?alt=media&token=b35f1e23-a123-4e78-bcd9-794222e95ed5) | ![App Screenshot 2](https://firebasestorage.googleapis.com/v0/b/filehostingvrn.appspot.com/o/files%2F3%2F7%2F2023%2C%209%3A45%3A49%20pm_Screenshot_20230703-212032.png?alt=media&token=24ba288e-dc38-43d9-b113-ed581817abed) | ![App Screenshot 3](https://firebasestorage.googleapis.com/v0/b/filehostingvrn.appspot.com/o/files%2F3%2F7%2F2023%2C%209%3A44%3A39%20pm_Screenshot_20230703-213127.png?alt=media&token=7354e185-adf8-4c07-b67a-2a975332bdb3) |
|--------------|--------------|--------------|
| Screenshot 4 | Screenshot 5 | Screenshot 6 |
| ![App Screenshot 4](https://firebasestorage.googleapis.com/v0/b/filehostingvrn.appspot.com/o/files%2F3%2F7%2F2023%2C%209%3A46%3A34%20pm_Screenshot_20230703-212046.png?alt=media&token=9e071b01-9093-456a-93a9-4c84aaf4f4e7) | ![App Screenshot 5](https://firebasestorage.googleapis.com/v0/b/filehostingvrn.appspot.com/o/files%2F3%2F7%2F2023%2C%209%3A49%3A15%20pm_Screenshot_20230703-212334.png?alt=media&token=3432bf33-65ac-4139-b04c-1c0f51684580) | ![App Screenshot 6](https://firebasestorage.googleapis.com/v0/b/filehostingvrn.appspot.com/o/files%2F3%2F7%2F2023%2C%209%3A53%3A28%20pm_Screenshot_20230703-212205.png?alt=media&token=23629076-4bbc-4b50-a403-41276328701e) |
|--------------|--------------|--------------|
| Screenshot 7 | Screenshot 8 | Screenshot 9 |
| ![App Screenshot 7](https://firebasestorage.googleapis.com/v0/b/filehostingvrn.appspot.com/o/files%2F3%2F7%2F2023%2C%209%3A54%3A39%20pm_Screenshot_20230703-212211.png?alt=media&token=25774131-c612-4b73-a6cf-1e114b087d8c) | ![App Screenshot 8](https://firebasestorage.googleapis.com/v0/b/filehostingvrn.appspot.com/o/files%2F3%2F7%2F2023%2C%209%3A55%3A28%20pm_Screenshot_20230703-212217.png?alt=media&token=0f46a6dd-af61-4815-96a3-7a952496ebde) | ![App Screenshot 9](https://firebasestorage.googleapis.com/v0/b/filehostingvrn.appspot.com/o/files%2F3%2F7%2F2023%2C%209%3A56%3A13%20pm_Screenshot_20230703-212222.png?alt=media&token=8be5942f-01e6-4fc8-88ca-af7f1018dba9) |
|--------------|--------------|--------------|
| Screenshot 10 | Screenshot 11 | Screenshot 12 |
| ![App Screenshot 10](https://firebasestorage.googleapis.com/v0/b/filehostingvrn.appspot.com/o/files%2F3%2F7%2F2023%2C%209%3A56%3A39%20pm_Screenshot_20230703-212229.png?alt=media&token=4f6e63c0-7a85-4650-98a6-1ab267f6ffa7) | ![App Screenshot 11](https://firebasestorage.googleapis.com/v0/b/filehostingvrn.appspot.com/o/files%2F3%2F7%2F2023%2C%209%3A57%3A44%20pm_Screenshot_20230703-212319.png?alt=media&token=ff10e934-3703-41b3-b707-380fc7b5258a) | ![App Screenshot 12](https://firebasestorage.googleapis.com/v0/b/filehostingvrn.appspot.com/o/files%2F3%2F7%2F2023%2C%209%3A58%3A14%20pm_Screenshot_20230703-212257.png?alt=media&token=aca74e2c-d40b-4fc2-b17c-820806ab073e) |
|--------------|--------------|--------------|
| Screenshot 13 | Screenshot 14 | Screenshot 15 |
| ![App Screenshot 13](https://firebasestorage.googleapis.com/v0/b/filehostingvrn.appspot.com/o/files%2F3%2F7%2F2023%2C%209%3A59%3A26%20pm_Screenshot_20230703-212103.png?alt=media&token=a5237c33-97f5-40c7-abbe-a859c48bc1e5) | ![App Screenshot 14](https://firebasestorage.googleapis.com/v0/b/filehostingvrn.appspot.com/o/files%2F3%2F7%2F2023%2C%2010%3A00%3A14%20pm_Screenshot_20230703-213204.png?alt=media&token=aa5ba77b-b462-4944-989f-d14b154862ba) | ![App Screenshot 15](https://firebasestorage.googleapis.com/v0/b/filehostingvrn.appspot.com/o/files%2F3%2F7%2F2023%2C%2010%3A01%3A05%20pm_Screenshot_20230703-213240.png?alt=media&token=bc2962f1-0c9a-406f-a173-d8c5cfb9db23) |


## Demo Watch on Youtube

[![Video Demo](https://img.youtube.com/vi/C2geDDoGGBc/0.jpg)](https://youtu.be/C2geDDoGGBc)



## Badges

Add badges from somewhere like: [shields.io](https://shields.io/)

[![MIT License](https://img.shields.io/badge/License-MIT-green.svg)](https://choosealicense.com/licenses/mit/)
[![GPLv3 License](https://img.shields.io/badge/License-GPL%20v3-yellow.svg)](https://opensource.org/licenses/)
[![AGPL License](https://img.shields.io/badge/license-AGPL-blue.svg)](http://www.gnu.org/licenses/agpl-3.0)

## How to Buy This

This project is not free. If you are interested in purchasing the rights and using it for production, please contact me via email or WhatsApp:

[![Email](https://img.icons8.com/fluency/48/000000/email.png)](mailto:official.vrnitsolution@gmail.com)
[![WhatsApp](https://img.icons8.com/fluency/48/000000/whatsapp.png)](https://wa.me/917058834216)


## Authors

- [@Varad Nikharage](https://github.com/varad8)
- [@Rushikesh Amberkar](https://github.com/Dada-Com)



![Logo](https://firebasestorage.googleapis.com/v0/b/filehostingvrn.appspot.com/o/files%2F3%2F7%2F2023%2C%209%3A14%3A56%20pm_VRNITSOLUTION%20(1).png?alt=media&token=d263ef8b-19bb-418a-819d-e55fb07b1180)

