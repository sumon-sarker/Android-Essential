# Android-Essential [Android Studio 3.0]
 - Async Load Image
```javascript
private class DownloadImageTask extends AsyncTask<String, Void, Bitmap> {
  ImageView bmImage;

  public DownloadImageTask(ImageView bmImage) {
      this.bmImage = bmImage;
  }

  protected Bitmap doInBackground(String... urls) {
      String urldisplay = urls[0];
      Bitmap mIcon11 = null;
      try {
        InputStream in = new java.net.URL(urldisplay).openStream();
        mIcon11 = BitmapFactory.decodeStream(in);
      } catch (Exception e) {
          Log.e("Error", e.getMessage());
          e.printStackTrace();
      }
      return mIcon11;
  }

  protected void onPostExecute(Bitmap result) {
      bmImage.setImageBitmap(result);
  }
}
```
And call from your `onCreate()` method using:
```javascript
new DownloadImageTask((ImageView) findViewById(R.id.imageView1))
        .execute(MY_URL_STRING);
```
Dont forget to add below permission in your manifest file

`<uses-permission android:name="android.permission.INTERNET"/>`
