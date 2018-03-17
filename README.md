# Android-Essential [Android Studio 3.0]

####  Save Session

     SharedPreferences SP = getSharedPreferences("AuthUser", Context.MODE_PRIVATE); /*0 = Private Mode*/
     SP.edit().putString("AuthUser",JO.toString()).commit();

     System.out.println("SP : "+ (SP.getString("AuthUser","")));
