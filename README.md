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



    private void preparelistdata(){

        AsyncHttpClient client  = new AsyncHttpClient();
        RequestParams params    = new RequestParams();
        params.put("key1", "value1");
        params.put("key2", "value2");
        -----------------------------

        String ApiURL = getString(R.string.api_base_url) + getString(R.string.api_teacher_enrolled_subjects_url);

        client.post(ApiURL,params, new JsonHttpResponseHandler(){
            @Override
            public void onStart() {
                progressDialog = new ProgressDialog(Attendances.this);
                progressDialog.setMessage("Loading your Subjects ...");
                progressDialog.setCancelable(false);
                progressDialog.show();
            }

            @Override
            public void onSuccess(int statusCode, Header[] headers, JSONObject response) {
                try {
                    if(response.getBoolean("status")==false){
                        progressDialog = new ProgressDialog(Attendances.this);
                        progressDialog.setMessage("Loading message here...");
                        progressDialog.setCancelable(false);
                        progressDialog.show();
                    }else{
                        attendanceModels = new ArrayList<>();
                        listView                = (ListView) findViewById(R.id.AttendanceListView);
                        JSONArray JA            = response.getJSONArray("response");
                        for (int i=0; i<JA.length(); i++){
                            JSONObject J        = JA.getJSONObject(i);
                            int subject_id      = J.getJSONObject("Subjects").getInt("id");
                            String subject      = J.getJSONObject("Subjects").getString("name");
                            int department_id   = J.getJSONObject("Departments").getInt("id");
                            String department   = J.getJSONObject("Departments").getString("name");
                            attendanceModels.add(new AttendanceModel(subject_id,subject,department_id,department));
                        }
                        attendanceAdapter= new AttendanceAdapter(Attendances.this,R.layout.teacher_attendance_list_view,attendanceModels);
                        listView.setAdapter(attendanceAdapter);

                        listView.setOnItemClickListener(new AdapterView.OnItemClickListener(){
                            @Override
                            public void onItemClick(AdapterView<?> adapterView, View view, int i, long l) {
                                AttendanceModel AM      = attendanceModels.get(i);
                                int subject_id          = AM.getSubject_id();
                                String subject          = AM.getSubject();
                                int department_id       = AM.getDepartment_id();
                                String department       = AM.getDepartment();
                                Intent I = new Intent(Attendances.this, AttendancesSet.class);
                                I.putExtra("subject_id",subject_id);
                                I.putExtra("subject",subject);
                                I.putExtra("department_id",department_id);
                                I.putExtra("department",department);
                                startActivity(I);
                            }
                        });
                    }
                } catch (JSONException e) {
                    e.printStackTrace();
                }
            }

            @Override
            public void onFailure(int statusCode, Header[] headers, String responseString, Throwable throwable) {
                //System.out.print("Result : Failed!");
            }

            @Override
            public void onProgress(long bytesWritten, long totalSize) {
                //System.out.print("Result : Progress!");
            }

            @Override
            public void onFinish() {
                progressDialog.hide();
            }
        });
    }
