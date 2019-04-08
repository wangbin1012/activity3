# activity3
安卓实验3
**第一题**

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190408225546749.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dhbmdiaW5fMTAxMg==,size_16,color_FFFFFF,t_70)
**核心代码:**
```java
package com.example.myapplication3;

import android.content.Context;
import android.support.annotation.NonNull;
import android.support.annotation.Nullable;
import android.view.LayoutInflater;
import android.view.View;
import android.view.ViewGroup;
import android.widget.ArrayAdapter;
import android.widget.ImageView;
import android.widget.TextView;

import java.util.List;

public class AnimalsAdapter extends ArrayAdapter {
    private int resourceId;
    public AnimalsAdapter(@NonNull Context context, int resource, @NonNull List<Animals> objects) {
        super(context, resource, objects);
        resourceId = resource;
    }

    @NonNull
    @Override
    public View getView(int position, @Nullable View convertView, @NonNull ViewGroup parent) {
        Animals animal = (Animals) getItem(position);
//        View view = LayoutInflater.from(getContext()).inflate(resourceId,parent,false);
//        提高List的运行效率，利用convertView对布局进行缓存
        View view;
        ViewHolder viewHolder;
        if(convertView == null){
            view = LayoutInflater.from(getContext()).inflate(resourceId,parent,false);
            viewHolder = new ViewHolder();
            viewHolder.animalsImage = (ImageView) view.findViewById(R.id.animals_image);
            viewHolder.animalsName = (TextView) view.findViewById(R.id.animals_name);
            view.setTag(viewHolder);
        }else{
            view = convertView;
            viewHolder = (ViewHolder) view.getTag();
        }
//        ImageView animalImage = (ImageView) view.findViewById(R.id.animals_image);
//        TextView animalName = (TextView) view.findViewById(R.id.animals_name);
//        animalImage.setImageResource(animal.getImagesId());
//        animalName.setText(animal.getName());
        viewHolder.animalsImage.setImageResource(animal.getImagesId());
        viewHolder.animalsName.setText(animal.getName());
        return view;
    }
    class ViewHolder{
        ImageView animalsImage;
        TextView animalsName;
    }
}
```

**截图：**
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190408220118246.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dhbmdiaW5fMTAxMg==,size_16,color_FFFFFF,t_70)

**第二题**
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190408220407402.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dhbmdiaW5fMTAxMg==,size_16,color_FFFFFF,t_70)
**核心代码：**
```java
package com.example.myapplication3;

import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.support.v7.app.AlertDialog;
import android.view.View;
import android.widget.Button;

public class AlterDialog extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        this.setTitle("AlterDialog");
        super.onCreate(savedInstanceState);
        setContentView(R.layout.button);
        Button button = (Button)findViewById(R.id.button);
        button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                AlertDialog builder = new AlertDialog.Builder(AlterDialog.this)
                        .setView(R.layout.dialog_layout)
                        .setNegativeButton("Cancel",null)
                        .setPositiveButton("Sign in",null)
                        .create();
                builder.show();
            }
        });


    }

}

```
**截图：**
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190408220522911.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dhbmdiaW5fMTAxMg==,size_16,color_FFFFFF,t_70)

**第三题**
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190408220752440.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dhbmdiaW5fMTAxMg==,size_16,color_FFFFFF,t_70)
**3、核心代码**
```java
package com.example.myapplication3;

import android.graphics.Color;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.Menu;
import android.view.MenuItem;
import android.widget.TextView;
import android.widget.Toast;

public class MenuActivity extends AppCompatActivity {

    @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        getMenuInflater().inflate(R.menu.menu,menu);
        return true;
    }

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        this.setTitle("XML定义菜单");
        super.onCreate(savedInstanceState);
        setContentView(R.layout.menu_layout);
    }

    @Override
    public boolean onOptionsItemSelected(MenuItem item) {
        TextView textView =(TextView) findViewById(R.id.text);
        switch (item.getItemId()){
            case R.id.z1:
                textView.setTextSize(10);break;
            case R.id.z2:
                textView.setTextSize(16);break;
            case R.id.z3:
                textView.setTextSize(20);break;
            case R.id.y1:
                textView.setTextColor(Color.RED);break;
            case R.id.y2:
                textView.setTextColor(Color.BLACK);break;
            case R.id.p:
                Toast.makeText(this,"这是普通单击项",Toast.LENGTH_SHORT).show();
                break;
            default:
        }
        return true;
    }
}
```
**截图：**
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190408221032125.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dhbmdiaW5fMTAxMg==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190408221049503.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dhbmdiaW5fMTAxMg==,size_16,color_FFFFFF,t_70)
**第四题**
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190408221250834.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dhbmdiaW5fMTAxMg==,size_16,color_FFFFFF,t_70)
**核心代码：**
```java
package com.example.myapplication3;

import android.support.annotation.Nullable;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.Menu;
import android.view.MenuInflater;
import android.view.MenuItem;
import android.view.View;
import android.widget.AbsListView;
import android.widget.AdapterView;
import android.widget.ListView;

import java.util.ArrayList;
import java.util.List;



public class ActionMode extends AppCompatActivity {
    private ListView listView;
    private List<Number> numberList = new ArrayList<>();
    @Override
    protected void onCreate(@Nullable Bundle savedInstanceState) {
        this.setTitle("ActionMode");
        super.onCreate(savedInstanceState);
        setContentView(R.layout.actionmode_layout);
        initNumber();
        NumberAdapter adapter = new NumberAdapter(ActionMode.this,R.layout.number_layout,numberList);
        listView = (ListView) findViewById(R.id.list_view2);
        listView.setAdapter(adapter);
        listView.setChoiceMode(ListView.CHOICE_MODE_MULTIPLE_MODAL);
        listView.setMultiChoiceModeListener(new AbsListView.MultiChoiceModeListener() {
            @Override
            public boolean onCreateActionMode(android.view.ActionMode mode, Menu menu) {
                MenuInflater inflater = mode.getMenuInflater();
                inflater.inflate(R.menu.actionmode, menu);
                return true;
            }

            @Override
            public boolean onPrepareActionMode(android.view.ActionMode mode, Menu menu) {
                return false;
            }

            @Override
            public boolean onActionItemClicked(android.view.ActionMode mode, MenuItem item) {
                mode.finish();
                return false;
            }

            @Override
            public void onDestroyActionMode(android.view.ActionMode mode) {

            }

            @Override
            public void onItemCheckedStateChanged(android.view.ActionMode mode, int position, long id, boolean checked) {
                mode.setTitle(listView.getCheckedItemCount()+" selected");
            }
        });
        listView.setOnItemClickListener(new AdapterView.OnItemClickListener() {
            @Override
            public void onItemClick(AdapterView<?> parent, View view,
                                    int position, long id) {

            }
        });
    }

    private void initNumber(){
        for(int i=0;i<1;i++){
            Number one = new Number("One",R.mipmap.ic_launcher);
            numberList.add(one);
            Number two = new Number("Two",R.mipmap.ic_launcher);
            numberList.add(two);
            Number three = new Number("Three",R.mipmap.ic_launcher);
            numberList.add(three);
            Number four = new Number("four",R.mipmap.ic_launcher);
            numberList.add(four);
            Number five = new Number("five",R.mipmap.ic_launcher);
            numberList.add(five);
        }
    }
}
```
**截图**
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190408221540385.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dhbmdiaW5fMTAxMg==,size_16,color_FFFFFF,t_70)
