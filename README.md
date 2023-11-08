<table>
  <tr>
    <th colspan="2">DATA MAHASISWA</th>
  </tr>
  <tr>
    <td>Nama</td>
    <td>Muhammad Arifin</td>
  </tr>
  <tr>
    <td>NIM</td>
    <td>312210330</td>
  </tr>
  <tr>
    <td>Kelas</td>
    <td>TI.22.A3</td>
  </tr>
</table>

# <p align="center">Membuat Program Menghitung Bilangan Fibonacci dengan Menambahkan Input Max Count</p>

# Fibonacci Sequence

Fibonacci Sequence (Deret angka Fibonacci) adalah deret angka yang diperoleh dengan menjumlahkan dua angka didepannya / sebelumnya:

      1, 1, 2, ... 1 + 2 = 3 ( 1, 1, 2, 3, ... ) 2 + 3 = 5 ( 1, 1, 2, 3, 5, ... ) 3 + 5 = 8 ( 1, 1, 2, 3, 5, 8, ... )

# 1. Membuat Button dan TextView Baru

- button restart(back)

- button max

- textView untuk input nilai maximalnya

 # Layout

 Pada layout ini, saya membuat tiga button dan satu textview :

- ```button_maksimum fibonacci```, berfungsi sebagai tombol “Set Limit” yang nantinya ketika di tekan akan muncul sebuah pop-up untuk masukan limit angka yang ingin kita hitung.

- ```button_count```, berfungsi sebagai tombol “count” yang nantinya ketika tombol ditekan akan menghitung bilangan fibonaccinya sesuai dengan yang kita limit. Juga berbeda warna pada setiap angka, agar tidak keliru.
  
- ```button_back```, berfungsi sebagai tombol back yang nantinya angka akan kembali ke awal.

- ```Textview show_count```, yang berfungsi untuk menampilkan angka atau bilangan fibonaccinya yang tepat berada di tengah.

Berikut adalah coding pada menu layout:

     <?xml version="1.0" encoding="utf-8"?>
      <androidx.constraintlayout.widget.ConstraintLayout
          xmlns:android="http://schemas.android.com/apk/res/android"
          xmlns:app="http://schemas.android.com/apk/res-auto"
          xmlns:tools="http://schemas.android.com/tools"
          android:layout_width="match_parent"
          android:layout_height="match_parent"
          tools:context=".MainActivity">
      
          <EditText
              android:id="@+id/edit_max_fibonacci"
              android:layout_width="0dp"
              android:layout_height="48dp"
              android:layout_marginEnd="8dp"
              android:layout_marginTop="8dp"
              android:hint="Maksimum Fibonacci"
              android:inputType="number"
              app:layout_constraintEnd_toEndOf="parent"
              app:layout_constraintTop_toTopOf="parent"
              tools:ignore="MissingTranslation"/>
      
          <Button
              android:id="@+id/button_toast"
              android:layout_width="190dp"
              android:layout_height="48dp"
              android:layout_marginStart="8dp"
              android:layout_marginTop="8dp"
              android:background="@color/colorPrimary"
              android:onClick="showToast"
              android:textColor="@android:color/white"
              android:text="@string/button_label_toast"
              app:layout_constraintStart_toStartOf="parent"
              app:layout_constraintTop_toTopOf="parent" />
      
      
          <Button
              android:id="@+id/button_count"
              android:layout_width="190dp"
              android:layout_height="48dp"
              android:layout_marginStart="8dp"
              android:layout_marginEnd="8dp"
              android:layout_marginBottom="8dp"
              android:background="@color/colorPrimary"
              android:onClick="countUp"
              android:text="@string/button_label_count"
              android:textColor="@android:color/white"
              app:layout_constraintBottom_toBottomOf="parent"
              app:layout_constraintEnd_toEndOf="parent"
              app:layout_constraintHorizontal_bias="0.0"
              app:layout_constraintStart_toStartOf="parent"
              tools:ignore="UsingOnClickInXml,VisualLintButtonSize" />
      
          <Button
              android:id="@+id/button_finish"
              android:layout_width="190dp"
              android:layout_height="48dp"
              android:layout_marginStart="8dp"
              android:layout_marginEnd="8dp"
              android:layout_marginBottom="8dp"
              android:background="@color/colorPrimary"
              android:onClick="back1"
              android:text="@string/button_label_finish"
              android:textColor="@android:color/white"
              app:layout_constraintBottom_toBottomOf="parent"
              app:layout_constraintEnd_toEndOf="parent"
              app:layout_constraintHorizontal_bias="1.0"
              app:layout_constraintStart_toStartOf="parent"
              tools:ignore="UsingOnClickInXml" />
      
          <TextView
              android:id="@+id/show_count"
              android:layout_width="0dp"
              android:layout_height="0dp"
              android:layout_marginStart="8dp"
              android:layout_marginTop="8dp"
              android:layout_marginEnd="8dp"
              android:layout_marginBottom="8dp"
              android:background="#FFFF00"
              android:gravity="center_vertical"
              android:text="@string/count_initial_value"
              android:textAlignment="center"
              android:textColor="@color/colorPrimary"
              android:textSize="160sp"
              android:textStyle="bold"
              app:layout_constraintBottom_toTopOf="@id/button_count"
              app:layout_constraintEnd_toEndOf="parent"
              app:layout_constraintStart_toStartOf="parent"
              app:layout_constraintTop_toBottomOf="@id/button_toast"
              tools:ignore="RtlCompat" />
      
      </androidx.constraintlayout.widget.ConstraintLayout>

  # Output

<img width="960" alt="Screenshot 2023-11-08 084305" src="https://github.com/marifinnnnn/UTS-pemrograman-mobile/assets/115518274/0b894739-59d7-4bbb-afa1-103b47bb06ba">

 # Java Class 

Pada Java class ```MainToast.java``` berisi semua coding untuk menjalankan aplikasi. Seperti fungsi untuk tombol-tombol, dialog set limit, warna yang berbeda pada setiap angka, lalu warna background yang bisa berubah dan rumus bilangan fibonacci. ```</androidx.constraintlayout.widget.ConstraintLayout>``` . Berikut adalah coding pada menu java :
      
       package com.hellotoast;
      
      import android.os.Bundle;
      import android.view.View;
      import android.widget.EditText;
      import android.widget.TextView;
      import android.widget.Toast;
      
      import androidx.appcompat.app.AppCompatActivity;
      
      public class MainToast extends AppCompatActivity {
          private TextView showCount;
          private int count = 0;
          private long fibNMinus1 = 1;
          private long fibNMinus2 = 0;
          private EditText edit_max_fibonacci;
      
          @Override
          protected void onCreate(Bundle savedInstanceState) {
              super.onCreate(savedInstanceState);
              setContentView(R.layout.activity_toast);
      
              showCount = findViewById(R.id.show_count);
              edit_max_fibonacci = findViewById(R.id.edit_max_fibonacci);
      
              updateCountDisplay();
      
              fibNMinus1 = 0;
              fibNMinus2 = 1;
          }
      
          private void updateCountDisplay() {
              showCount.setText(String.valueOf(fibNMinus2));
      
              if (count % 4 == 0) {
                  showCount.setTextColor(getResources().getColor(R.color.colorPrimary));
              } else if (count % 4 == 1) {
                  showCount.setTextColor(getResources().getColor(R.color.colorAccent));
              } else if (count % 4 == 2) {
                  showCount.setTextColor(getResources().getColor(R.color.colorPrimary));
              } else {
                  showCount.setTextColor(getResources().getColor(R.color.colorAccent));
              }
          }
      
          public void showToast(View view){
              Toast.makeText(this, "Bilangan Fibonacci",
                      Toast.LENGTH_SHORT).show();
          }
      
          public void countUp(View view) {
              int maxFibonacci = Integer.parseInt(edit_max_fibonacci.getText().toString());
      
              if (count >= maxFibonacci) {
                  Toast.makeText(this, "Maksimum Fibonacci tercapai", Toast.LENGTH_SHORT).show();
                  return;
              }
      
              long fibCurrent;
              if (count == 0 || count == 0) {
                  fibCurrent = 1;
              } else {
                  fibCurrent = fibNMinus1 + fibNMinus2;
              }
      
              fibNMinus2 = fibNMinus1;
              fibNMinus1 = fibCurrent;
              updateCountDisplay();
      
              count++;
          }
      
          public void back1(View view) {
              count = 1;
              fibNMinus1 = 1;
              fibNMinus2 = 0;
              updateCountDisplay();
          }
      }     

  # Output

<img width="960" alt="Screenshot 2023-11-08 085305" src="https://github.com/marifinnnnn/UTS-pemrograman-mobile/assets/115518274/e249e3dd-de75-4ac4-ae5b-2c400939064b">


## Masukkan Angka Maksimum Fibonacci

<img width="960" alt="Screenshot 2023-11-08 085627" src="https://github.com/marifinnnnn/UTS-pemrograman-mobile/assets/115518274/0fd49647-2a59-45f4-92fb-af4a0e3f2fcf">


## Kemudian Klik ```Count```
<img width="960" alt="Screenshot 2023-11-08 085627" src="https://github.com/marifinnnnn/UTS-pemrograman-mobile/assets/115518274/a70b5550-ad30-429c-8a2b-a5b9da67820c">

<img width="960" alt="Screenshot 2023-11-08 093454" src="https://github.com/marifinnnnn/UTS-pemrograman-mobile/assets/115518274/bce72ea7-a42a-44a7-9a24-ecde792a06f2">

![fibonacci](https://github.com/marifinnnnn/UTS-pemrograman-mobile/assets/115518274/3dc3bbe0-8def-4611-b51b-9db53c57f108)

<img width="960" alt="Screenshot 2023-11-08 094225" src="https://github.com/marifinnnnn/UTS-pemrograman-mobile/assets/115518274/80174a9e-0112-4c1a-8083-6b712aba8480">

<img width="960" alt="Screenshot 2023-11-08 094237" src="https://github.com/marifinnnnn/UTS-pemrograman-mobile/assets/115518274/8e6bb470-0b40-40de-8433-56ea2dd5ca64">


## Ini Adalah Tampilan Ketika Sudah Mencapai Maksimum Fibonacci 

![fibonacci2](https://github.com/marifinnnnn/UTS-pemrograman-mobile/assets/115518274/e987ae25-f00b-45a1-bed9-83c2c2f5f77d)


## Ini adalah Tampilan Ketika Kita Mengklik ```Back```

![fibonacci BACK](https://github.com/marifinnnnn/UTS-pemrograman-mobile/assets/115518274/b83c7b6e-dccc-4e54-8746-362d15615ebb)
