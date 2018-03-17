# Android-Essential [Android Studio 3.0]

####  Intent [Pass Data]
 
    /*Called when the user clicks the Send button*/
    public void sendMessage(View view) {
        Intent intent     = new Intent(this, DisplayMessageActivity.class);
        EditText editText = (EditText) findViewById(R.id.edit_message);
        String message    = editText.getText().toString();
        intent.putExtra(EXTRA_MESSAGE, message);
        startActivity(intent);
    }

####  Intent [Pass Data]

/*Called when the user clicks the Send button*/
public void sendMessage(View view) {
    Intent intent     = new Intent(YourCurrentClassName.this, AnotherClassActivity.class);
    EditText editText = (EditText) findViewById(R.id.edit_message);
    String message    = editText.getText().toString();
    intent.putExtra(EXTRA_MESSAGE, message);
    startActivity(intent);
}
