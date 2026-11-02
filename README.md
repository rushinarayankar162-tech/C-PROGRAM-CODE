#include <stdio.h>
#include <conio.h>
#include <dos.h>

#define HEIGHT 18

void draw_frame(int robot_y)
{
    int y;

    clrscr();

    textcolor(YELLOW);
    gotoxy(25, 2);
    cprintf("LINE FOLLOWER ROBOT");

    textcolor(LIGHTGREEN);
    gotoxy(5, 4);
    cprintf("START");
    gotoxy(65, 4);
    cprintf("END");

    /* Draw the track edges and center line */
    for (y = 0; y < HEIGHT; ++y)
    {
        textcolor(LIGHTGREEN);
        gotoxy(5, 6 + y);
        cprintf("|");
        gotoxy(75, 6 + y);
        cprintf("|");

        textcolor(WHITE);
        gotoxy(40, 6 + y);
        cprintf("#");
    }

    /* Draw the robot centered over the line */
    textcolor(LIGHTCYAN);
    gotoxy(36, 6 + robot_y);
    cprintf(".--------.");
    gotoxy(36, 7 + robot_y);
    cprintf("| ROBOT  |");
    gotoxy(36, 8 + robot_y);
    cprintf("O---#----O");

    textcolor(YELLOW);
    gotoxy(5, 25);
    cprintf("Robot moving from START to END...");
}

int main(void)
{
    int position;

    for (position = HEIGHT - 1; position >= 0; --position)
    {
        draw_frame(position);
        delay(250);
    }

    clrscr();

    textcolor(YELLOW);
    gotoxy(25, 2);
    cprintf("LINE FOLLOWER ROBOT");

    gotoxy(28, 12);
    cprintf("Robot reached the END!");

    getch();
    return 0;
}# C-PROGRAM-CODE
