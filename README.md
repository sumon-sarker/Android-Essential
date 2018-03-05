####  Model Class {Student}
```javascript
package com.example.sumon.{APP_NAME_HERE}.student;

public class Student {
    public String name;
    public String phone;

    public Student(String name, String phone) {
        this.name  = name;
        this.phone = phone;
    }
}
```

####  Adapter Class {UserAdapter}
```javascript
package com.example.sumon.{APP_NAME_HERE}.student;

public class UserAdapter extends ArrayAdapter<Student> {

    public UserAdapter(@NonNull Context context, int resource, @NonNull List<Student> objects) {
        super(context, resource, objects);
    }

    @Override
    public View getView(int position, @Nullable View convertView, @NonNull ViewGroup parent) {

        Student student = getItem(position);

        if (convertView == null){
            convertView = LayoutInflater.from(getContext()).inflate(R.layout.student_row_layout, parent, false);
        }

        TextView name   = (TextView) convertView.findViewById(R.id.name);
        TextView phone  = (TextView) convertView.findViewById(R.id.phone);

        name.setText(student.name);
        phone.setText(student.phone);

        //return super.getView(position, convertView, parent);
        return convertView;
    }
}
```
