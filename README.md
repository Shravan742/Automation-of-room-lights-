
#include<LiquidCrystal.h>;
LiquidCrystal lcd(12,11,5,4,3,2);

#define in 14
#define out 19
int Pin[4]={10,9,8};
int i;

int count=0;

void IN()
{
    count++;
    lcd.clear();
    lcd.print("Person In Room:");
    lcd.setCursor(0,1);
    lcd.print(count);
    delay(1000);
}
void OUT()
{
  count--;
    lcd.clear();
    lcd.print("Person In Room:");
    lcd.setCursor(0,1);
    lcd.print(count);
    delay(1000);
}

void setup()
{
  lcd.begin(16,2);
  lcd.print("Visitor Counter");
  delay(2000);
  pinMode(in, INPUT);
  pinMode(out, INPUT);
for(i=0;i<3;i++){
  pinMode(Pin[i], OUTPUT);}
  lcd.clear();
  lcd.print("Person In Room:");
  lcd.setCursor(0,1);
  lcd.print(count);
}

void loop()
{  
  
  if(digitalRead(in))
  IN();
  if(digitalRead(out))
  OUT();
  
  if(count<=0)
  {
    lcd.clear();
    digitalWrite(Pin[1], LOW);
digitalWrite(Pin[2], LOW);
digitalWrite(Pin[3], LOW);
    lcd.clear();
    lcd.print("Nobody In Room:");
    lcd.setCursor(0,1);
}}
