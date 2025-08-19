Fee Management Portal 
  
📖 Overview
This project is a simple, secure, and serverless web application designed to help manage student fee payments for the Emmanuel School of Theology. This tool allows a designated administrator to enter payment details, save them permanently to a private cloud database, and generate a professional PDF receipt modeled after the official school receipt.

To allow for public demonstration and testing, the application also includes a Guest Mode. This feature allows any visitor to try the application's functionality without accessing or interfering with the private administrative data, as all guest entries are stored in a separate, temporary collection.

✨ Key Features
Secure Admin Login: The main application is protected by a username and password to ensure that all financial data remains private and secure.

Separate Guest Mode: Visitors can explore the application's features in a sandboxed environment. Guest data is completely separate from admin data.

Persistent & Secure Data Storage: All records are saved online using Google Firebase's Firestore, a powerful NoSQL cloud database. This ensures data is never lost, even if the browser is closed or the computer is shut down.

Dynamic PDF Receipt Generation: Instantly generates and downloads a professional-looking PDF receipt for each new entry using the jsPDF library.

Real-time History View: The "Payment History" tab displays all saved records and updates instantly whenever a change is made to the database.

Modern & Simple UI: The user interface is built with Tailwind CSS for a clean, responsive, and easy-to-use experience on any device.

Serverless Deployment: The entire application is a single index.html file, making it incredibly lightweight and easy to deploy for free on modern hosting platforms like Netlify.

🛠️ Technologies Used
This project was built with a modern, serverless architecture, making it fast, scalable, and cost-effective.

Frontend:

HTML5: The core structure of the web page.

Tailwind CSS: A utility-first CSS framework for rapid UI development.

JavaScript: Powers all the application's logic, including user interaction, data handling, and PDF generation.

Backend & Database (Firebase):

Firebase Firestore: A flexible, scalable NoSQL cloud database used to store all student payment records securely. Its real-time nature means data is synced across all clients instantly.

Firebase Authentication: Used to enable a simple, anonymous sign-in session that secures the database rules, ensuring only logged-in users can access the data.

Deployment (Netlify):

Netlify: A modern hosting platform that makes it incredibly simple to deploy websites directly from a GitHub repository. Netlify handles the entire build and deployment process, providing a live, shareable URL for the application.

PDF Generation:

jsPDF & jsPDF-AutoTable: JavaScript libraries used to dynamically create and customize the client-side PDF receipts.

🚀 How to Set Up
To run this project, you need to connect it to your own free Firebase backend.

1. Clone the Repository
First, get the code on your local machine:

git clone [https://github.com/SudevSamuel07/Fee-Paying-Website-for-college.git](https://github.com/SudevSamuel07/Fee-Paying-Website-for-college.git)
cd Fee-Paying-Website-for-college

2. Create a Firebase Project
Go to the Firebase Console and sign in with your Google account.

Click "Add project", give it a name (e.g., "FeeTrackerApp"), and continue. You can disable Google Analytics.

Once the project is created, click the web icon (</>) to "Add an app" and select "Web".

Give your app a nickname and click "Register app".

Firebase will provide you with a firebaseConfig object. Copy this entire object.

3. Configure the Application
Open the index.html file in your code editor.

Find the firebaseConfig object in the <script type="module"> section.

Paste your unique firebaseConfig object that you copied from Firebase, replacing the placeholder keys.

4. Configure Firebase Services
In your Firebase project, go to the Build > Authentication section.

Click the "Sign-in method" tab.

Click on "Anonymous" from the list of providers, enable the toggle switch, and click Save.

Next, go to the Build > Firestore Database section.

Click "Create database" and start in test mode. Choose a server location close to you.

Go to the "Rules" tab in Firestore and replace the existing rules with the following to enable secure data separation:

rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    // Admin data is private
    match /students_admin/{docId} {
      allow read, write: if request.auth != null;
    }

    // Guest data is public
    match /students_guest/{docId} {
      allow read, write: if request.auth != null;
    }
  }
}

Click "Publish".

Your application is now fully configured and ready to use!

💻 How to Use
Open the index.html file in your web browser or visit the live Netlify URL.

You will be presented with the login screen:

For Admin Access: Enter the username and password set inside the index.html file. This will give you access to the private admin data.

For Guest Access: Click the "Continue as Guest" button. This will give you access to a separate, public database for testing.

🌐 Deployment with Netlify
You can host this website for free.

Push your updated code (with your Firebase keys) to your GitHub repository.

Sign up for a free account at Netlify using your GitHub account.

Click "Add new site" > "Import from Git".

Select your GitHub repository.

The default deployment settings will work perfectly. Click "Deploy site".

Netlify will provide you with a live URL for your application.

