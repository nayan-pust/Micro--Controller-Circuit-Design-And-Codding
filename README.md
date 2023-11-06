# Micro--Controller-Circuit-Design-And-Codding

# 2 digit seven Segment interfacing--------

  **Circuit**
  ![image](https://github.com/nayan-pust/Micro--Controller-Circuit-Design-And-Codding/assets/114688354/1ac97018-f110-44ba-8455-68ded2d06ff4)
# Code---
```ruby
  char Array_CA[]={0xC0,0xF9,0xA4,0xB0,0x99,0x92,0x82,0xF8,0x80,0x90};

void main()

{
  int i,k,mod=0,res=0;
   TRISD=0x00;
  TRISC=0x00;
  TRISB=0x00;
  portb=0x00;
  portd=0x00;

  portd.f1=0x00;

  while(1)
    {
        for(i=0;i<=99;i++)
        {

           res=i/10;
           mod=i%10;
             for(k=1;k<=50;k++)
               {
                   portc.f0=1;
                   portb=Array_CA[res];
                   delay_ms(10);
                   portc.f0=0;
                   portc.f1=1;
                   portb=Array_CA[mod];
                   delay_ms(10);
                   portc.f1=0;
               }

          }

     }
}


```

# Seven Segment two digit controll with button----
# Circuit
![image](https://github.com/nayan-pust/Micro--Controller-Circuit-Design-And-Codding/assets/114688354/19b5e2cb-95b4-4ce3-88bb-771c4a171535)
File- 

# Code
```ruby
char arraycc[] = { 0xBF, 0x86, 0xDB, 0xCF, 0xE6, 0xED, 0xFD, 0x87, 0xFF, 0xEF };
char on_array[] = {0x3F,  0x37};
char off_array[]= { 0x40,0x40};



void main() {
    int i;
   int  bt_zero = 0, bt_one = 0, first_load_time,second_load_time,res,mod,k;





   TRISB = 0x00;
   TRISC = 0x00;
   TRISD.f0 = 0xff;
   TRISD.f1 = 0xff;
   TRISD.f2 = 0xff;
   TRISD.f3 = 0xff;
   TRISD.f4 = 0x00;
   TRISD.f5 = 0x00;
   portb = 0x00;
   portc = 0x00;
   portd.f4=0x00;
   portd.f5=0x00;

   while(1)
   {

        if(portd.f1 == 0xff)  // click initialize
       {
          delay_ms(150);
          if(portd.f1 == 0xff)  // click stability check
          {
              bt_zero++;        // digit increment
              if(bt_zero == 10) // after 9, next is 0
              {
                 bt_zero = 0;
              }
          }
       }
       if(portd.f0 == 0xff)
       {
          delay_ms(150);
          if(portd.f0 == 0xff)
          {
              bt_one++;
              if(bt_one == 10)
              {
                 bt_one = 0;
              }
          }
       }

       first_load_time = (bt_zero * 10 + bt_one);
       portc.f0 = 0x00;
       portb = arrayCC[bt_zero];
       delay_ms(10);
       portc.f0 = 0xff;

       portc.f1 = 0x00;
       portb = arrayCC[bt_one];
       delay_ms(10);
       portc.f1 = 0xff;


}
}

```

# 4 Digit seven segment count 3 digit number....
**Circuit**

![image](https://github.com/nayan-pust/Micro--Controller-Circuit-Design-And-Codding/assets/114688354/78bfd66d-82aa-4a75-9f67-1a914be92eaf)

```ruby
// 4 Digit 7 segment LED for COMMON CATHODE
char ArrayCC[]={0x3F,0x06,0x5B,0x4F,0x66,0x6D,0x7D,0x07,0x7F,0x6F};
void main()
{
    int button1=0,button2=0,button3=0,button4=0;
    int i,right,mid,lst,k;
    TRISD=0xff;
    TRISB=0x00;
    TRISC=0x00;
    portb=0x00;
    portd=0x00;
    while(1)
    {

  while(1)
    {
        for(i=1;i<=100;i++)
        {

             right = i / 100;
              mid = (i / 10) % 10;
              lst = i% 10;
             for(k=1;k<=10;k++)
               {
                   portc.f3=0;
                   portb=ArrayCC[lst];
                   delay_ms(3);
                   portc.f3=1;
                   portc.f2=0;
                   portb=ArrayCC[mid];
                   delay_ms(3);
                   portc.f2=1;
                   portc.f1=0;
                   portb=ArrayCC[right];
                   delay_ms(3);
                   portc.f1=1;
               }

          }

     }
}
    }

```





