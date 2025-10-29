# Ex.No:2(b) To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## AIM:

To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## EQUIPMENTS REQUIRED:

Latest Version Android Studio

## ALGORITHM:

Step 1: Start App & Display First Screen Launch the app. Show the first screen (MainActivity) with: EditText for user input (number) Button labeled “Factorial”

Step 2: Get User Input User enters a number in the EditText. When the “Factorial” button is clicked: Read the number from EditText. Validate input (check if it’s not empty and is a positive integer).

Step 3: Use Explicit Intent to Open Second Screen Create an Explicit Intent to start the second activity (ResultActivity). Intent intent = new Intent(MainActivity.this, ResultActivity.class); Pass the number to the second screen using Intent extras:

intent.putExtra("number", inputNumber);
Start the second activity: startActivity(intent);

Step 4: Second Screen Receives Number In ResultActivity’s onCreate() method: Get the number from Intent:

int num = getIntent().getIntExtra("number", 0);
Step 5: Calculate Factorial

Initialize factorial = 1. Loop from 1 to num:

for (int i = 1; i <= num; i++) {
    factorial *= i;
}
Or use BigInteger if large numbers.

Step 6: Display Result Show the factorial in a TextView on the second screen.

Step 7: Optional Enhancements Handle invalid inputs (empty or negative numbers) with a Toast message. Use ScrollView if the factorial result is large. Use BigInteger for very large numbers to prevent overflow.


## PROGRAM:
```
/*
Program to print the text “ExplicitIntent”.
Developed by: KARTHICK S
Registeration Number : 212224230114
*/
```
### ACTIVITY_MAIN.XML
```python
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <EditText
        android:id="@+id/numberEditText1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="172dp"
        android:ems="10"
        android:inputType="textPersonName"
        android:minHeight="48dp"
        android:text=""
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.497"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        tools:ignore="LabelFor,TextFields,SpeakableTextPresentCheck"
        android:autofillHints="" />

    <Button
        android:id="@+id/factorialButton"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="340dp"
        android:text="Button"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.498"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        tools:ignore="HardcodedText" />

</androidx.constraintlayout.widget.ConstraintLayout>
```
### ACTIVITY_MAIN.XML
```python
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout        xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity3">

    <TextView
        android:id="@+id/factorialTextView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="283dp"
        android:text="TextView"
        android:textSize="36sp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        tools:ignore="HardcodedText" />
</androidx.constraintlayout.widget.ConstraintLayout>
```
### MAINACTIVITY.JAVA

```python
package com.example.explicit_indent;

import android.content.Intent;
import android.os.Bundle;
import android.widget.Button;
import android.widget.EditText;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    private EditText numberEditText;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        numberEditText = findViewById(R.id.numberEditText1);
        Button factorialButton = findViewById(R.id.factorialButton);

        factorialButton.setOnClickListener(v -> {
            int number = Integer.parseInt(numberEditText.getText().toString());

            Intent intent = new Intent(MainActivity.this, MainActivity3.class);
            intent.putExtra("number", number);
            startActivity(intent);
        });
    }
}
```
### MAINACTIVITY3.JAVA

```python
public class MainActivity3 extends AppCompatActivity {

    @SuppressLint("SetTextI18n")
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main3);

        TextView factorialTextView = findViewById(R.id.factorialTextView);

        Intent intent = getIntent();
        int number = intent.getIntExtra("number", 0);

        long factorial = calculateFactorial(number);
        factorialTextView.setText("Factorial of " + number + " is " + factorial);
    }

    private long calculateFactorial(int number) {
        long factorial = 1;
        for (int i = 1; i <= number; i++) {
            factorial *= i;
        }
        return factorial;
    }
}
```


## OUTPUT

![inputintent](https://github.com/yuvaraj-csk/ExplicitIntent-MAD/assets/134052574/adb07288-8518-40ac-9618-eb94524e2f81)
![answerintent](https://github.com/yuvaraj-csk/ExplicitIntent-MAD/assets/134052574/bba8be59-2e8f-490b-ab89-87d3a8dc1a05)
<img src="https://github.com/yuvaraj-csk/ExplicitIntent-MAD/assets/134052574/5683094f-89c2-4b97-80e5-7dbfb7fe8d0e" width="300" height="400" alt="Description of the image">


## RESULT
Thus a Simple Android Application create a Explicit Intents using Android Studio is developed and executed successfully.


