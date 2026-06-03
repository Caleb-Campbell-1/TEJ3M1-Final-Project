// C++ code
//
// created 26 Mar 2026
// by Caleb Campbell
// This code runs a half-adder with two LEDs on a breadboard
// AND inputs
const int andA = 2;
const int andB = 3;
const int andOut = 9;

// XOR inputs
const int xorA = 4;
const int xorB = 5;
const int xorOut = 8;
int A = 0;
int B = 0;
void setup()
{
  // send inputs to chips
  Serial.begin(9600);
  pinMode(andA, OUTPUT);
  pinMode(andB, OUTPUT);
  pinMode(xorA, OUTPUT);
  pinMode(xorB, OUTPUT);
  // output from chips to LEDs
  pinMode(andOut, INPUT);
  pinMode(xorOut, INPUT);
}

void loop()
{
  // loop will cycle through all inputs
  for (int a = 0; a <=1; a++){
    for (int b = 0; b <=1; b++){ 
      digitalWrite(andA, a);
      digitalWrite(andB, b);
      digitalWrite(xorA, a);
      digitalWrite(xorB, b);
      delay(1000); // Wait for 1000 millisecond(s)
     
      Serial.print("Half adder - Output");
        int A = digitalRead(xorOut);
      int B = digitalRead(andOut);
      // Half-adder sum and carry
     int sum = a ^ b;
     int carry = a & b;  
      delay(1000); // Wait for 1000 millisecond(s)
      // print to serial monitor
      Serial.print("  A:");
      Serial.print(A); 
       Serial.print("  B:");
      Serial.print(B); 
      Serial.print("  sum=");
      Serial.print(sum);
      Serial.print("  carry=");
      Serial.print(carry);
      Serial.println();
      delay(1000); // Wait for 1000 millisecond(s)
    }
  }
}
