# Android-Essential [Android Studio 3.0]

####  Spinner [Initialize Spinner Data]
 
     public class SomeClass extends AnotherActivityClass {
     
         public String[] plants = new String[]{
          "Lace flower",
          "Sugar maple",
          "Mountain mahogany",
          "Butterfly weed"
        };
        
        protected void onCreate(Bundle savedInstanceState) {
          super.onCreate(savedInstanceState);
          setContentView(R.layout.activity_dashboard);
          
          final Spinner Divisions   = (Spinner) findViewById(R.id.Divisions);
          
          /*Create and Initialize ArrayList*/
          List<String> plantsList = new ArrayList<>(Arrays.asList(plants));

          /*Initializing an ArrayAdapter*/
          ArrayAdapter<String> spinnerArrayAdapter = new ArrayAdapter<String>(
                  this,R.layout.support_simple_spinner_dropdown_item,plantsList);
          
          /*Set the Adapter for List Items*/
          Divisions.setAdapter(spinnerArrayAdapter);

          /*Change Action Event*/
          Districts.setOnItemSelectedListener(new AdapterView.OnItemSelectedListener() {
              @Override
              public void onItemSelected(AdapterView<?> adapterView, View view, int i, long l) {
                  String S = Districts.getSelectedItem().toString();
                  System.out.println("Getting Value :" + S);
              }

              @Override
              public void onNothingSelected(AdapterView<?> adapterView) {
                  System.out.println("Hey : Nothing is selected");
              }
          });
          
       }
    }
