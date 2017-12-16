---
title: Android布局实验
tags:  Android,布局,基础
---

## 实验一

![enter description here][1]

#### 部分代码
```java
<?xml version="1.0" encoding="utf-8"?>
<android.support.constraint.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    >

    <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
        android:orientation="vertical"
        android:layout_width="fill_parent"
        android:layout_height="fill_parent"
        >
        <!-- 定义一个List -->
        <ListView android:id="@+id/mylist"
            android:layout_width="fill_parent"
            android:layout_height="wrap_content"
            />
        <LinearLayout android:orientation="horizontal"
            android:layout_width="fill_parent"
            android:layout_height="fill_parent">
        <!-- 定义一个ImageView，用于作为列表项的一部分。 -->
        <!-- 定义一个TextView，用于作为列表项的一部分。 -->
        <TextView android:id="@+id/name"
            android:layout_width="80dp"
            android:layout_height="50dp"
            android:textSize="16dp"
            android:layout_alignParentLeft="true"
            android:gravity="center_vertical"
            android:paddingLeft="10dp"
            />
            <ImageView android:id="@+id/imag"
            android:layout_width="50dp"
            android:layout_height="50dp"
            android:layout_alignParentRight="true"
            android:paddingLeft="10dp"
            android:layout_marginLeft="250dp"
            />
            </LinearLayout>
    </LinearLayout>


</android.support.constraint.ConstraintLayout>

```
#### 实验截图

![enter description here][2]

## 实验二
![enter description here][3]


#### 部分代码
```java
package com.example.dell.dialog;

import android.content.DialogInterface;
import android.support.v7.app.AlertDialog;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.LinearLayout;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        final Button bn = (Button)findViewById(R.id.bn);
        final AlertDialog.Builder builder = new AlertDialog.Builder(this);
        bn.setOnClickListener(new View.OnClickListener(){
            @Override
            public void onClick(View v) {
                LinearLayout linerout = (LinearLayout)getLayoutInflater().inflate(R.layout.login,null);
                builder.setView(linerout);
                builder.setNegativeButton("Cancel", new DialogInterface.OnClickListener() {
                    @Override
                    public void onClick(DialogInterface dialog, int which) {

                    }
                });
                builder.setPositiveButton("Sign in", new DialogInterface.OnClickListener() {
                    @Override
                    public void onClick(DialogInterface dialog, int which) {

                    }
                });
                builder.show();
            }
        });

    }
}

```
#### 实验截图

![enter description here][4]

## 实验三

![enter description here][5]

#### 部分代码
```java
package com.example.dell.menutest;

import android.graphics.Color;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.Menu;
import android.view.MenuItem;
import android.view.SubMenu;
import android.view.ViewConfiguration;
import android.widget.EditText;
import android.widget.Toast;

import java.lang.reflect.Field;

public class MainActivity extends AppCompatActivity {
    final int Font_10 = 1;
    final int Font_16 = 2;
    final int Font_20 = 3;
    final int Plain_Item = 4;
    final int Font_red = 5;
    final int Font_black =6;
    private EditText edit;
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        edit = (EditText)findViewById(R.id.et);
    }


    public boolean onCreateOptionsMenu(Menu menu){
        SubMenu fontMenu = menu.addSubMenu("字体大小");
        fontMenu.setHeaderTitle("选择字体大小");
        fontMenu.add(0,Font_10,0,"10号字体");
        fontMenu.add(0,Font_16,0,"16号字体");
        fontMenu.add(0,Font_20,0,"20号字体");
        menu.add(0,Plain_Item,0,"普通菜单选项");
        SubMenu colorMenu = menu.addSubMenu("字体颜色");
        colorMenu.setHeaderTitle("选择字体颜色");
        colorMenu.add(0,Font_red,0,"红色");
        colorMenu.add(0,Font_black,0,"黑色");
        return super.onCreateOptionsMenu(menu);
    }
    public boolean onOptionsItemSelected(MenuItem mi){
        switch (mi.getItemId()){
            case Font_10:
                edit.setTextSize(10*2);
                break;
            case Font_16:
                edit.setTextSize(16*2);
                break;
            case Font_20:
                edit.setTextSize(20*2);
                break;
            case Plain_Item:
                Toast toast=Toast.makeText(MainActivity.this,"点击普通菜单选项",Toast.LENGTH_SHORT);
                toast.show();
                break;
            case Font_red:
                edit.setTextColor(Color.RED);
                break;
            case Font_black:
                edit.setTextColor(Color.BLACK);
                break;
        }
        return
                true;
    }

}

```
#### 实验截图

![enter description here][6]


  [1]: ./1.png "1"
  [2]: ./2.png "2"
  [3]: ./3.png "3"
  [4]: ./4.png "4"
  [5]: ./5.png "5"
  [6]: ./6.png "6"