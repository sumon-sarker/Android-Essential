# Android-Essential [Android Studio 3.0]

####  Save Session
     
     ProgressDialog progressDialog;
     
     ......

     progressDialog = new ProgressDialog(YourClassName.this); /*getActivity()*/
     progressDialog.setMessage("Signing in ...");
     progressDialog.setCancelable(false);
     progressDialog.show();
