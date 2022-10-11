Thank you for this repo :)
Please contribute any program here.


// SUDOKU SOLVER //

class Solution {
public:
    bool issafe(vector<vector<char>> &bd, int i, int j, char ch)
{
    for (int k = 0; k < 9; k++)
    {
        if (bd[k][j] == ch)
            return 0;
    }
    for (int k = 0; k < 9; k++)
    {
        if (bd[i][k] == ch)
            return 0;
    }

    int r = i - i % 3;
    int c = j - j % 3;
    for (int x = 0; x < 3; x++)
    {
        for (int y = 0; y < 3; y++)
        {
            if (bd[r + x][c + y] == ch)
                return 0;
        }
    }

    return 1;
}

bool sl(vector<vector<char>> &bd, int i, int j)
{
    if (i == 9)
        return 1;
    if (j == 9)
    {
        return sl(bd, i + 1, 0);
    }
    if (bd[i][j] != '.')
    {
        return sl(bd, i, j + 1);
    }

    for (char ch = '1'; ch <= '9'; ch++)
    {
        if (issafe(bd, i, j, ch))
        {
            bd[i][j] = ch;
            if (sl(bd, i, j + 1))
                return 1;
            bd[i][j] = '.';
        }
    }
    return 0;
}

void solveSudoku(vector<vector<char>> &bd)
{
    sl(bd, 0, 0);
}
};

//-----------------------------------------------------------------------------------------------------------------------------------------------------------------//
//MARIO GAME IN C LANGUAGE//

#include <cs50.h>
#include <stdio.h>

int get_positive_int(string prompt);

int main(void)

{
    int number = get_positive_int("Height: "); 
   
    for (int height = 0; height < number; height++) 
    {
        for (int dots = number - height - 2; dots >= 0; dots--)
        {
            printf(" "); //printing dots for visibility, then remove to space
        }
        for (int row = 0; row <= height; row++) //loop for rows
        {
            printf("#");
        }
        printf("\n");
    }
}


int get_positive_int(string prompt) 
{
    int number; 
    do 
    {
        number = get_int("%s", prompt);
    }
    while (number < 1 || number > 8); 
    return number; 
}
