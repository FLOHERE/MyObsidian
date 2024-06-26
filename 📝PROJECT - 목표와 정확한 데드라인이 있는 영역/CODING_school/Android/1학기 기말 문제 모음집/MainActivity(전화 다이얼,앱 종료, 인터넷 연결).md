![[Pasted image 20240626193855.png]]


```xml
<?xml version="1.0" encoding="utf-8"?>  
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    tools:context=".MainActivity">
	  
    <Button  
        android:id="@+id/Button1"  
        android:text="전화 다이얼 이동"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content" />  
		  
    <Button  
        android:id="@+id/Button2"  
        android:text="인터넷(다음) 이동"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content" />  
		  
    <Button  
        android:id="@+id/Button3"  
        android:text="앱 종료"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content" />  
		  
    <Button  
        android:id="@+id/Button4"  
        android:text="이미지 회전"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content" />  
		  
    <Button  
        android:id="@+id/Button5"  
        android:text="나이 계산"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content" />  
		  
    <Button  
        android:id="@+id/Button6"  
        android:text="언어 체크"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content" />  
</LinearLayout>
```

```java
package com.example.hahyeonsu;  
  
import androidx.appcompat.app.AppCompatActivity;  
  
import android.content.Intent;  
import android.net.Uri;  
import android.os.Bundle;  
import android.view.View;  
import android.widget.Button;  
  
public class MainActivity extends AppCompatActivity {  
  
    Button Button1, Button2, Button3, Button4, Button5, Button6;  
  
    @Override  
    protected void onCreate(Bundle savedInstanceState) {  
        super.onCreate(savedInstanceState);  
        setContentView(R.layout.activity_main);  
  
        Button1 = findViewById(R.id.Button1);  
        Button2 = findViewById(R.id.Button2);  
        Button3 = findViewById(R.id.Button3);  
        Button4 = findViewById(R.id.Button4);  
        Button5 = findViewById(R.id.Button5);  
        Button6 = findViewById(R.id.Button6);  
  
        // 암시적 인텐트 전화 다이얼  
        Button1.setOnClickListener(new View.OnClickListener() {  
            @Override  
            public void onClick(View v) {  
                Uri uri = Uri.parse("tel:01071426173");  
                Intent phone = new Intent(Intent.ACTION_DIAL, uri);  
                startActivity(phone);  
            }        
        });  
        // 암시적 인텐트 인터넷(다음)  
        Button2.setOnClickListener(new View.OnClickListener() {  
            @Override  
            public void onClick(View v) {  
                Intent daum = new Intent(Intent.ACTION_VIEW, Uri.parse("https://daum.net"));  
                startActivity(daum);  
            }       
         });  
        // 앱 종료  
        Button3.setOnClickListener(view ->{  
            finish();  
        });  
        // 이미지 회전 화면 전환  
        Button4.setOnClickListener(new View.OnClickListener() {  
            @Override  
            public void onClick(View v) {  
                Intent imgpage = new Intent(getApplicationContext(),subImagePage.class);  
                startActivity(imgpage);  
            }        
        });  
        // 나이 계산 화면 전환  
        Button5.setOnClickListener(new View.OnClickListener() {  
            @Override  
            public void onClick(View v) {  
                Intent agecal = new Intent(getApplicationContext(),subAgeCal.class);  
                startActivity(agecal);  
            }        
        });  
        // 언어 선택 화면 전환  
        Button6.setOnClickListener(new View.OnClickListener() {  
            @Override  
            public void onClick(View v) {  
                Intent lagcheck = new Intent(getApplicationContext(),lagcheck.class);  
                startActivity(lagcheck);  
            }       
         });    
    }
}
```
