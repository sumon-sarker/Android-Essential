# Android-Essential [Android Studio 3.0]

    JSONArray SaveData = new JSONArray();
    JSONObject data    = new JSONObject();
    
    for (YourModel ASM : YourModelData){
      try {
          data.put("key1", "Value1");
          data.put("key2", "Value2");
          data.put("key3", "Value3");
          ---
      } catch (JSONException e) {
          e.printStackTrace();
      }
      SaveData.put(data);
   }
