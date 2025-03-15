``` C#
using System;
class HelloWorld {
  static void Main() {
    int Screen = new int [8192];
    Act_pos = 0;
    int KBD = 0;
    while(true){
      if(KBD !=0){
        Screen[Act_pos] = 1;
        if(Act_pos <= 8192)
        Act_pos++;

        }  
        else if (KBD ==0 ){
        Screen[Act_pos] = -1; 
        if(Act_pos >= 0)
        Act_pos=Act_pos - 1;
        }
    }
    
  }
}
```
