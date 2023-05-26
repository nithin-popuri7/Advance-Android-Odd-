# Ex.No:5 Develop a simple application for proximity sensor using Sensor Manager in android studio.


## AIM:

To develop a sensor application for proximity sensor using sensor manager in Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Min.required Artic Fox)

## ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as proximitysensor and click Next. 

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml.

Step 6: Display process of proximitysensor in android mobile devices.

Step 7: Save and run the application.

## PROGRAM:
```
Program to print the process of proximitysensor in android mobile devices”.
Developed by:P.Siva Naga Nithin
Registeration Number:212221240037
```
## AndroidManifest.xml:
```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    package="com.example.proximitysensor">

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.ProximitySensor"
        tools:targetApi="31">
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>
```
## MainActivity.java
```
import android.hardware.SensorEventListener;
import android.hardware.SensorManager;
import android.os.Bundle;
import android.widget.TextView;
import android.widget.Toast;
public class MainActivity extends AppCompatActivity {
    TextView sensorStatusTV;
    SensorManager sensorManager;
    Sensor proximitySensor;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        sensorStatusTV = findViewById(R.id.sensorStatusTV);
        sensorManager = (SensorManager) getSystemService(Context.SENSOR_SERVICE);
        proximitySensor = sensorManager.getDefaultSensor(Sensor.TYPE_PROXIMITY);
        if (proximitySensor == null) {
            Toast.makeText(this, "No proximity sensor found in device.", Toast.LENGTH_SHORT).show();
            finish();
        } else {
            Toast.makeText(this,"Proximity sensor is found",Toast.LENGTH_LONG).show();
            sensorManager.registerListener(proximitySensorEventListener,
                    proximitySensor,
                    SensorManager.SENSOR_DELAY_NORMAL);
        }
    }
    SensorEventListener proximitySensorEventListener = new SensorEventListener() {
        @Override
        public void onAccuracyChanged(Sensor sensor, int accuracy) {
        }
        @Override
        public void onSensorChanged(SensorEvent event) {
            if (event.sensor.getType() == Sensor.TYPE_PROXIMITY) {
                if (event.values[0] == 0) {
                    sensorStatusTV.setText("Near");
                } else {
                    sensorStatusTV.setText("Away");
                }
            }
        }
    };
}
```
## activity_main.xml:
```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/sensorStatusTV"
        android:layout_width="fill_parent"
        android:layout_height="wrap_content"
        android:layout_centerInParent="true"
        android:textAlignment="center"
        android:textSize="50dp" />



</RelativeLayout>
```

## OUTPUT:
![6](https://github.com/nithin-popuri7/Advance-Android-Odd-/assets/94154780/4f0d0835-f722-4c15-a2c3-9fc72e4289a4)

![6 1](https://github.com/nithin-popuri7/Advance-Android-Odd-/assets/94154780/5e71a480-6d06-4015-bc08-e579b986abcb)

![6 2](https://github.com/nithin-popuri7/Advance-Android-Odd-/assets/94154780/a30170f7-b400-47ea-a5b4-3ef65569d724)

![6 3](https://github.com/nithin-popuri7/Advance-Android-Odd-/assets/94154780/bf0a4688-a7c9-4e30-9f68-7595d348e74a)

![6 4](https://github.com/nithin-popuri7/Advance-Android-Odd-/assets/94154780/bdfc878d-2494-4dd6-8172-bd0791f9ea0f)








## RESULT:
Thus a Simple Android Application to display the details of proximity sensor using sensor manager in Android Studio is developed and executed successfully.
