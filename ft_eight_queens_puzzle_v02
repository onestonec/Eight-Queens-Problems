#include <stdio.h>
#include <time.h>

int check_diag(int *board, int guess, int current_col)
{
    int i = 0;
    int move = 1;
    int col_diag = i + move;
    int row_up_diag = board[i] - move;
    int row_dn_diag = board[i] + move;
    
    while (i < 8)
    {
        while ((col_diag  < 8) && ((row_up_diag >= 0) || (row_dn_diag < 8)))
        {
            if ((col_diag == current_col) && ((row_up_diag == guess) || (row_dn_diag == guess)))
            {
                return 0;
            } else
            {
                move++;
            }
            col_diag = i + move ;
            row_up_diag = board[i] - move;
            row_dn_diag  = board[i] + move;
        }
        i++;
        move = 1;
        col_diag = i + move ;
        row_up_diag = board[i] - move;
        row_dn_diag  = board[i] + move;
    }
    return 1;
}

int check_row(int *row, int guess, int current_col)
{
    int i = 0;

    while (i < 8)
    {
        if (row[i] == guess)
            return 0; 
        else
            i++;
    }
    return 1;
}


int solver(int *row, int *possibilities)
{
    int i = 0;
    int j = 0;
    int guess = 0;

    while (i < 8)
    {
        if(row[i] < 0)
        {
          while (guess < 8)
          {
              if ((check_row(row, guess, i) == 1) && (check_diag(row, guess, i) == 1))
              {
                  row[i] = guess;
                  solver(row, possibilities);
              } 
              guess++;
          }
          row[i] = -1;
          return 0;
        }
        else
            i++;
    }
    *possibilities = *possibilities + 1;
    while(j < 8)
    {
        printf("%d", row[j]);
        j++;
    }
    printf("\n");
    return 1;
}


int ft_eight_queens_puzzle(void)
{
    int row[8] = {-1,-1,-1,-1,-1,-1,-1,-1};
    int possibilities = 0;

    solver(row, &possibilities);

    return possibilities;
}

int main (void)
{
    // to store the execution time of code
    double time_spent = 0.0;
 
    clock_t begin = clock();
    printf("%d\n", ft_eight_queens_puzzle());
    clock_t end = clock();
 
    // calculate elapsed time by finding difference (end - begin) and
    // dividing the difference by CLOCKS_PER_SEC to convert to seconds
    time_spent += (double)(end - begin) / CLOCKS_PER_SEC;
 
    printf("The elapsed time is %f seconds", time_spent);
    return 0;
}
