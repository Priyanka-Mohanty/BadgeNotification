# BadgeNotification

# XML :
    <?xml version="1.0" encoding="utf-8"?>
    <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/activity_main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:paddingBottom="@dimen/activity_vertical_margin"
    android:paddingLeft="@dimen/activity_horizontal_margin"
    android:paddingRight="@dimen/activity_horizontal_margin"
    android:paddingTop="@dimen/activity_vertical_margin"
    android:orientation="vertical">

    <EditText
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter number"
        android:text=""
        android:id="@+id/input"
        android:inputType="number"/>
    <RelativeLayout
        android:layout_margin="@dimen/activity_horizontal_margin"
        android:id="@+id/relative_layout"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_gravity="center"
        android:gravity="center">

        <ImageView
            android:id="@+id/img_notification"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:src="@mipmap/ic_notification" />

        <TextView
            android:id="@+id/badge_notification_count"
            style="@style/TextTitleStyleNotification"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_alignRight="@+id/img_notification"
            android:text="1" />
    </RelativeLayout>
    </LinearLayout>


# javaCode:

        package com.example.priyankam.badgenotification;

        import android.support.v7.app.AppCompatActivity;
        import android.os.Bundle;
        import android.text.Editable;
        import android.text.TextWatcher;
        import android.view.View;
        import android.widget.EditText;
        import android.widget.ImageView;
        import android.widget.TextView;

        public class MainActivity extends AppCompatActivity {

        String STRING_ZERO = "0";
        String value;
        @Override
        protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        final EditText editInputText=(EditText)findViewById(R.id.input);
        ImageView imgNotification = (ImageView) findViewById(R.id.img_notification);
        final TextView textBadgeAlarmCount = (TextView) findViewById(R.id.badge_notification_count);


        editInputText.addTextChangedListener(new TextWatcher() {
            @Override
            public void beforeTextChanged(CharSequence charSequence, int i, int i1, int i2) {

            }

            @Override
            public void onTextChanged(CharSequence charSequence, int i, int i1, int i2) {
                //set  badge Count
                value=editInputText.getText().toString().trim();
                if(value.equals(Integer.parseInt(STRING_ZERO))
                        ||value.isEmpty()){
                    textBadgeAlarmCount.setVisibility(View.GONE);
                } else {
                    textBadgeAlarmCount.setVisibility(View.VISIBLE);
                    textBadgeAlarmCount.setText(value);
                }
            }

            @Override
            public void afterTextChanged(Editable editable) {

            }
            });
            }
        }


![Output](https://raw.githubusercontent.com/Priyanka-Mohanty/BadgeNotification/master/layout-2017-02-13-150524.png)
