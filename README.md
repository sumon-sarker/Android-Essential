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

####  Fragment Class {Students}
```javascript
package com.example.sumon.{APP_NAME_HERE};

public class Students extends Fragment {

    ArrayList<Student> studentList;
    ListView LV;
    UserAdapter usersAdapter;

    public Students() {
        /*CONFIG HERE*/
    }

    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container,
                             Bundle savedInstanceState) {
        // Inflate the layout for this fragment
        return inflater.inflate(R.layout.fragment_students, container, false);
    }

    @Override
    public void onViewCreated(View view, @Nullable Bundle savedInstanceState) {
        super.onViewCreated(view, savedInstanceState);
        studentList = new ArrayList<>();
        LV          = (ListView) view.findViewById(R.id.StudentList);

        studentList.add(new Student("Name 1", "Phone 1"));
        studentList.add(new Student("Name 2", "Phone 2"));
        studentList.add(new Student("Name 3", "Phone 3"));
        studentList.add(new Student("Name 4", "Phone 4"));
        studentList.add(new Student("Name 5", "Phone 5"));

        usersAdapter= new UserAdapter(getActivity(),R.layout.{CUSTOM_LAYOUT_ID_HERE},studentList);
        LV.setAdapter(usersAdapter);
    }
}

```
