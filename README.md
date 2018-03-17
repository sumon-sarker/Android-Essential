# Android-Essential [Android Studio 3.0]

####  AsyncTask [Network request]
 
   public class UserLoginTask extends AsyncTask<Void, Void, Boolean> {

        private final String field1;
        private final String field2;

        UserLoginTask(String email, String password) {
            field1  = email;
            field2  = password;
        }

        @Override
        protected Boolean doInBackground(Void... params) {
            /*TODO: attempt authentication against a network service.*/
            try {
                /*Simulate network access here.*/
            } catch (InterruptedException e) {
                return false;
            }
            /*Get the response and process here*/
            /*TODO: register the new account here.*/
            return true;
        }

        @Override
        protected void onPostExecute(final Boolean success) {
            mAuthTask = null;
            showProgress(false);
            if (success) {
                finish();
            } else {
                mPasswordView.setError(getString(R.string.error_incorrect_password));
                mPasswordView.requestFocus();
            }
        }

        @Override
        protected void onCancelled() {
            mAuthTask = null;
            showProgress(false);
        }
    }
