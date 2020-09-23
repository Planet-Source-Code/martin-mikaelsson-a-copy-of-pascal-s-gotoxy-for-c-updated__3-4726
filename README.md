<div align="center">

## A copy of PASCAL:s GOTOXY for C\+\+ \(UPDATED\)


</div>

### Description

The same way like PASCALs GotoXY. It let you place the textcursor anywhere on the console_screen.

UPDATE (2002-12-5) now shows how to use GotoXY

in loops.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Martin Mikaelsson](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/martin-mikaelsson.md)
**Level**          |Beginner
**User Rating**    |4.6 (23 globes from 5 users)
**Compatibility**  |Microsoft Visual C\+\+
**Category**       |[Strings](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/strings__3-26.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/martin-mikaelsson-a-copy-of-pascal-s-gotoxy-for-c-updated__3-4726/archive/master.zip)

### API Declarations

```
#include <iostream.h>
#include <conio.h>
#include <stdio.h>
#include <windows.h>
#include <winbase.h>
```


### Source Code

```
//***************************************************************
//
// GOTOXY.CPP
//
// When I programmed in PASCAL for 2 years ago I find the command
// GotoXY; very useful in my programs.
// But in C++ "GotoXY; only existed on Borland C++!!!!!!!!
// So, my dad and I have made an own GotoXY and it takes two
// parameters.
//
// And by the way... I'm swedish.
//
// Snillet98
//
//***************************************************************
#include <iostream.h>
#include <conio.h>
#include <stdio.h>
#include <windows.h>
#include <winbase.h>
void GOTOXY ( WORD y, WORD x);
HANDLE  hStdIn;
HANDLE  hStdOut;
CONSOLE_SCREEN_BUFFER_INFO csbiInfo;
int main()
{
	GOTOXY(2,2);	// Set textcursor to Y = 2 and X = 2
	cout << "Writing here now" << endl;
	GOTOXY(3,3);
	cout << "And now here" << endl;
	GOTOXY(4,4);
	cout << "What? Now I came here!" << endl;
	GOTOXY(5,5);
	cout << "Jump, jump, jump" << endl;
	printf("%s \n", "Press any key to continue");
	getch();
	GOTOXY(2,2);	// This string will overwrite the first string
	cout << "Ops! Now I owerwrite someting!" << endl;
	GOTOXY(6,0);
	printf("%s \n", "Press any key to continue");
	getch();
	system("CLS");
	for(int i=0;i<20;i++)
	{
		GOTOXY(i,i*2);
		printf("*");
	}
	return 0;
}
void GOTOXY ( WORD y, WORD x)	// This is GOTOXY function with two parameters
{
	hStdOut = GetStdHandle(STD_OUTPUT_HANDLE);
	hStdIn = GetStdHandle(STD_INPUT_HANDLE);
	GetConsoleScreenBufferInfo( hStdOut, &csbiInfo );
	COORD coordScreen;
	coordScreen.X = x;
 	coordScreen.Y = y;
 	(void) SetConsoleCursorPosition(hStdOut, coordScreen);
}
// No much comments here but I think you understand the most of this code
// NOTE! This is my first code I upload here. So please, tell me how good it is.
```

