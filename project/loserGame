//seyedsadramousavi77@gmail.com
#include <stdio.h>
#include <stdlib.h>
#include "clui-master\clui.h"
#include <string.h>
#include <time.h>

int valid_password(char pass[50]);
void menu2(char username[50], int);
int number_of_words();
void change_points(char user[50], int);
void loser_game1(char username[50], int, char word[50], int);
void loser_game2(char username[50], int, char word[50], int);
void leaderBoard();
void change_password(char username[50], char password[50]);

typedef struct
{
    char user_name[50];
    char password[50];
    int point;
} login;

int main()
{
    int a = 0, b = 0;

    login moshakhasat;

    while (1)
    {

        while (1)
        {
            clear_screen();
            change_color_rgb(20, 150, 40);
            printf("####      ## ##    ## ##   ### ###  ### ##             ## ##     ##     ##   ##  ### ###\n");
            printf("##      ##   ##  ##   ##   ##  ##   ##  ##           ##   ##     ##     ## ##    ##  ##\n");
            printf("##      ##   ##  ####      ##       ##  ##           ##        ## ##   # ### #   ##\n");
            printf("##      ##   ##   #####    ## ##    ## ##            ##  ###   ##  ##  ## # ##   ## ##\n");
            printf("##      ##   ##      ###   ##       ## ##            ##   ##   ## ###  ##   ##   ##\n");
            printf("##  ##  ##   ##  ##   ##   ##  ##   ##  ##           ##   ##   ##  ##  ##   ##   ##  ##\n");
            printf("### ###   ## ##    ## ##   ### ###  #### ##            ## ##   ###  ##  ##   ##  ### ###\n\n");
            reset_color();
            change_color_rgb(250, 200, 30);
            printf("1.Login\n2.Signup\n3.Exit\n");
            reset_color();

            scanf("%d", &a);

            if (a == 1)
            {
                FILE *file = fopen("names.txt", "r"), *file1;
                if (file == NULL)
                {
                    change_color_rgb(250, 200, 30);
                    printf("There is no account yet. Please signup first then try again.\n");
                    reset_color();
                    fclose(file);
                    delay(5000);
                    break;
                }
                change_color_rgb(250, 200, 30);
                printf("please enter your username and password:\n");
                reset_color();
                scanf("%s", moshakhasat.user_name);
                scanf("%s", moshakhasat.password);

                char temp_user[200][2000];
                char temp_pass[200][2000];

                while (1)
                {
                    int m, n, flag = 0;
                    for (int i = 0;; i++)
                    {
                        if (feof(file))
                        {
                            change_color_rgb(250, 200, 30);
                            printf("Your password or username was wrong. Try again.\nIf you have not signed up yet please sign up first.\n\n");
                            reset_color();
                            delay(6000);
                            break;
                        }
                        fscanf(file, "%s   %s", temp_user[i], temp_pass[i]);

                        m = strcmp(temp_user[i], moshakhasat.user_name);
                        n = strcmp(temp_pass[i], moshakhasat.password);

                        if (m == 0 && n == 0)
                        {
                            fclose(file);
                            flag = 1;
                            menu2(moshakhasat.user_name, moshakhasat.point);
                            break;
                        }
                    }

                    break;
                }
            }

            else if (a == 2)
            {
                change_color_rgb(250, 200, 30);
                printf("enter a user name for yourself:");
                reset_color();
                int flag = 0, input = 0;
                FILE *file = fopen("names.txt", "a+");
                FILE *file1 = fopen("leaderboard.txt", "a+");
                FILE *file2 = fopen("names.txt", "r");
                while (1)
                {
                    if (feof(file2) && flag == 1)
                    {
                        fclose(file2);
                        change_color_rgb(250, 200, 30);
                        printf("You have been verified. Please go to login.\n");
                        reset_color();
                        delay(5000);
                        break;
                    }

                    else if (feof(file2) && flag == 0)
                    {
                        fclose(file2);
                        break;
                    }

                    if (input == 0)
                    {
                        scanf("%s", moshakhasat.user_name);
                        input = 1;
                    }

                    char temp[50];
                    fscanf(file2, "%s", temp);

                    int n = strcmp(moshakhasat.user_name, temp);

                    if (n == 0)
                    {
                        flag = 1;
                    }
                }

                if (flag == 1)
                {
                    break;
                }

                fprintf(file, "%s", moshakhasat.user_name);
                fprintf(file1, "%s   ", moshakhasat.user_name);
                change_color_rgb(250, 200, 30);
                printf("enter a valid password:");
                reset_color();
                while (1)
                {
                    scanf("%s", moshakhasat.password);
                    b = valid_password(moshakhasat.password);

                    if (b != 1)
                    {
                        change_color_rgb(250, 200, 30);
                        printf("\npassword you have entered is not valid\nyour password should contain small and capital letters, numbers and especial characters(@, !,..).\nAlso your password should be at least 8 letters.\nplease enter a valid password:");
                        reset_color();
                    }

                    else
                    {
                        fprintf(file, "    %s\n", moshakhasat.password);
                        fclose(file);
                        fprintf(file1, "%d\n", moshakhasat.point);
                        fclose(file1);
                        fclose(file2);
                        menu2(moshakhasat.user_name, moshakhasat.point);
                        break;
                    }
                }
            }

            else if (a == 3)
            {
                change_color_rgb(250, 200, 30);
                clear_screen();
                char a[150] = "Hope you enjoyed. Developed by Seyed Sadra Mousavi. :)))))";
                int tedad = strlen(a);
                for (int i = 0; i < tedad; i++)
                {
                    printf("%c", a[i]);
                    delay(100);
                }
                reset_color();
                delay(1000);
                return 0;
            }
        }
    }
}

int valid_password(char pass[50])
{
    int m = strlen(pass);

    int num = 0, small = 0, capital = 0, especiall = 0;

    for (int i = 0; i < m; i++)
    {
        if (pass[i] >= 48 && pass[i] <= 57)
        {
            num = 1;
        }

        else if ((pass[i] >= 33 && pass[i] <= 47) || pass[i] == 64)
        {
            especiall = 1;
        }

        else if (pass[i] >= 65 && pass[i] <= 90)
        {
            capital = 1;
        }

        else if (pass[i] >= 97 && pass[i] <= 122)
        {
            small = 1;
        }
    }

    if (small == 1 && capital == 1 && especiall == 1 && num == 1 && m >= 8)
    {
        return 1;
    }

    else
    {
        return 0;
    }
}

void menu2(char username[50], int points)
{
    int a = 0;

    while (1)
    {
        clear_screen();
        change_color_rgb(20, 150, 40);
        printf("####      ## ##    ## ##   ### ###  ### ##             ## ##     ##     ##   ##  ### ###\n");
        printf("##      ##   ##  ##   ##   ##  ##   ##  ##           ##   ##     ##     ## ##    ##  ##\n");
        printf("##      ##   ##  ####      ##       ##  ##           ##        ## ##   # ### #   ##\n");
        printf("##      ##   ##   #####    ## ##    ## ##            ##  ###   ##  ##  ## # ##   ## ##\n");
        printf("##      ##   ##      ###   ##       ## ##            ##   ##   ## ###  ##   ##   ##\n");
        printf("##  ##  ##   ##  ##   ##   ##  ##   ##  ##           ##   ##   ##  ##  ##   ##   ##  ##\n");
        printf("### ###   ## ##    ## ##   ### ###  #### ##            ## ##   ###  ##  ##   ##  ### ###\n\n");
        reset_color();
        change_color_rgb(250, 200, 30);
        printf("1.Start game\n2.Show leaderboard\n3.New word\n4.Change password\n5.Exit\n");
        reset_color();
        scanf("%d", &a);

        if (a == 1)
        {
            FILE *file = fopen("words.txt", "r");
            if (file == NULL)
            {
                change_color_rgb(250, 200, 30);
                printf("You have to add word first.");
                reset_color();
                delay(5000);
            }
            else
            {
                FILE* file5 = fopen("words.txt" , "r");
                int t = 1 , flag = 0;
                char check[50];
                while (t > 0)
                {
                    if(fscanf(file5 , "%s" , check) == EOF)
                    {
                        change_color_rgb(250, 200, 30);
                        printf("There is no words yet. Please add word first.\n");
                        flag = 1;
                        fclose(file5);
                        delay(5000);
                        reset_color();
                    }
                    t--;
                }

                if(flag == 0)
                {
                    int tedad = number_of_words();

                    int entekhabi = (rand() % tedad) + 1;
                    char word[50];

                    for (int i = 1; i <= entekhabi; i++)
                    {
                        fscanf(file, "%s", word);
                    }

                    fclose(file);

                    int tedad2 = strlen(word);

                    if (tedad2 < 8)
                    {
                        int point = strlen(word);
                        loser_game1(username, point, word, tedad2);
                    }

                    else
                    {
                        int point = strlen(word);
                        loser_game2(username, point, word, tedad2);
                    }
                }
            }
        }

        else if (a == 2)
        {
            leaderBoard();
        }

        else if (a == 3)
        {
            FILE *file = fopen("words.txt", "r");

            if (file == NULL)
            {
                fclose(file);

                file = fopen("words.txt", "w");
                change_color_rgb(250, 200, 30);
                printf("please enter your suggestion:");
                reset_color();
                char suggestion_word[50];
                scanf("%s", suggestion_word);

                fprintf(file, "%s\n", suggestion_word);

                int points_word = strlen(suggestion_word);

                change_points(username, points_word);

                change_color_rgb(250, 200, 30);
                printf("\nThank you for your suggestion.You have points of this word.\n");
                reset_color();

                delay(5000);
                fclose(file);
            }

            else
            {
                fclose(file);
                while (1)
                {
                    file = fopen("words.txt", "r+");
                    char suggestion_word[50];
                    int flag = 0;

                    change_color_rgb(250, 200, 30);
                    printf("please enter your suggestion word:");
                    reset_color();
                    scanf("%s", suggestion_word);

                    while (1)
                    {
                        if (feof(file))
                        {
                            break;
                        }
                        char temp[50];

                        fscanf(file, "%s", temp);

                        int m = strcmp(temp, suggestion_word);

                        if (m == 0)
                        {
                            flag = 1;
                        }
                    }

                    if (flag == 1)
                    {
                        change_color_rgb(250, 200, 30);
                        printf("your suggestion already exists.\n");
                        reset_color();
                        fclose(file);
                    }

                    else if (flag == 0)
                    {
                        fprintf(file, "%s\n", suggestion_word);
                        fclose(file);

                        int points_word = strlen(suggestion_word);

                        change_points(username, points_word);

                        change_color_rgb(250, 200, 30);
                        printf("Thank you for suggestion.You have points of this word.\n");
                        reset_color();

                        delay(5000);
                        break;
                    }
                }
            }
        }

        else if (a == 4)
        {
            change_color_rgb(250, 200, 30);
            printf("Please enter your new password:");
            reset_color();
            char new_pass[50];
            scanf("%s", new_pass);

            int a = valid_password(new_pass);

            if (a == 0)
            {
                change_color_rgb(250, 200, 30);
                printf("Your suggestion was not valid.");
                delay(3500);
                reset_color();
            }

            else
            {
                change_color_rgb(250, 200, 30);
                change_password(username, new_pass);
                printf("Your password changed succesfully.\n");
                delay(3500);
                reset_color();
            }
        }

        else if (a == 5)
        {
            break;
        }
    }
}

int number_of_words()
{
    FILE *file = fopen("words.txt", "r");

    int num = 0;

    while (1)
    {
        char temp[50];
        if (fscanf(file, "%s", temp) == EOF)
        {
            break;
        }
        num++;
    }

    return num;
}

void change_points(char user[50], int points)
{
    FILE *file, *temp;
    file = fopen("leaderboard.txt", "r");
    temp = fopen("temp_leaderboard.txt", "w");

    char names[50];
    int pts;

    while (!feof(file))
    {
        fscanf(file, "%s   %d\n", names, &pts);
        int m = strcmp(names, user);

        if (m == 0)
        {
            fprintf(temp, "%s   %d\n", names, pts + points);
        }

        else
        {
            fprintf(temp, "%s   %d\n", names, pts);
        }
    }

    fclose(file);
    fclose(temp);

    remove("leaderboard.txt");
    rename("temp_leaderboard.txt", "leaderboard.txt");
}

void loser_game1(char username[50], int points, char word[50], int tedad)
{
    char jakhali[50], estefade_shode[50];
    for (int i = 0; i < tedad; i++)
    {
        jakhali[i] = '-';
        printf("%c ", jakhali[i]);
    }
    int check = 0, loser = 0, check_estefade = 0, estefade = 0, tedad_estefade = 0;
    while (1)
    {
        int flag = 0;
        check_estefade = 0;
        clear_screen();
        change_color_rgb(20, 150, 40);
        if (loser == 1)
        {
            printf("####\n");
            printf("##\n");
            printf("##\n");
            printf("##\n");
            printf("##\n");
            printf("##  ##\n");
            printf("### ###\n");
        }

        else if (loser == 2)
        {
            printf("####      ## ##\n");
            printf("##      ##   ##\n");
            printf("##      ##   ##\n");
            printf("##      ##   ##\n");
            printf("##      ##   ##\n");
            printf("##  ##  ##   ##\n");
            printf("### ###   ## ##\n");
        }

        else if (loser == 3)
        {
            printf("####      ## ##    ## ##\n");
            printf("##      ##   ##  ##   ##\n");
            printf("##      ##   ##  ####   \n");
            printf("##      ##   ##   ##### \n");
            printf("##      ##   ##      ###\n");
            printf("##  ##  ##   ##  ##   ##\n");
            printf("### ###   ## ##    ## ##\n");
        }

        else if (loser == 4)
        {
            printf("####      ## ##    ## ##   ### ###\n");
            printf("##      ##   ##  ##   ##   ##  ## \n");
            printf("##      ##   ##  ####      ##     \n");
            printf("##      ##   ##   #####    ## ##  \n");
            printf("##      ##   ##      ###   ##     \n");
            printf("##  ##  ##   ##  ##   ##   ##  ## \n");
            printf("### ###   ## ##    ## ##   ### ###\n");
        }
        reset_color();
        change_color_rgb(250, 200, 30);
        printf("\n\n\n");
        for (int i = 0; i < tedad; i++)
        {
            printf("%c ", jakhali[i]);
        }
        reset_color();
        char test = getch();

        check = 0;
        if (estefade == 0)
        {
            estefade_shode[tedad_estefade] = test;
            tedad_estefade++;
            estefade = 1;

            for (int i = 0; i < tedad; i++)
            {
                if (test == word[i])
                {
                    jakhali[i] = test;
                    check = 1;
                }
            }

            if (check == 0)
            {
                loser++;
            }
        }

        else if (estefade == 1)
        {
            for (int i = 0; i < tedad_estefade; i++)
            {
                if (estefade_shode[i] == test)
                {
                    change_color_rgb(250, 200, 30);
                    printf("\n\nYou have already use this letter. You have used this letters till now:");

                    for (int i = 0; i < tedad_estefade; i++)
                    {
                        printf(" %c", estefade_shode[i]);
                    }
                    reset_color();
                    delay(3000);
                    check_estefade = 1;
                    break;
                }
            }

            if (check_estefade == 1)
            {
                continue;
            }

            else
            {
                estefade_shode[tedad_estefade] = test;
                tedad_estefade++;
            }

            for (int i = 0; i < tedad; i++)
            {
                if (test == word[i])
                {
                    jakhali[i] = test;
                    check = 1;
                }
            }

            if (check == 0)
            {
                loser++;
            }

            for (int i = 0; i < tedad; i++)
            {
                if (jakhali[i] == '-')
                {
                    flag = 1;
                }
            }
            if (flag == 0)
            {
                clear_screen();

                change_color_rgb(20, 150, 40);
                printf("##   ##    ####   ###  ##  ###  ##  ### ###  ### ##\n");
                printf("##   ##     ##      ## ##    ## ##   ##  ##   ##  ##\n");
                printf("##   ##     ##     # ## #   # ## #   ##       ##  ##\n");
                printf("## # ##     ##     ## ##    ## ##    ## ##    ## ## \n");
                printf("# ### #     ##     ##  ##   ##  ##   ##       ## ## \n");
                printf(" ## ##      ##     ##  ##   ##  ##   ##  ##   ##  ##\n");
                printf("##   ##    ####   ###  ##  ###  ##  ### ###  #### ##\n");
                reset_color();

                char a[100] = "YOU WON. CONGRATULATION. THE WORD WAS: ";
                int b = strlen(a);
                change_color_rgb(250, 200, 30);
                printf("\n");
                for (int i = 0; i < b; i++)
                {
                    printf("%c", a[i]);
                    delay(100);
                }

                for (int i = 0; i < tedad; i++)
                {
                    printf("%c", word[i]);
                    delay(100);
                }

                reset_color();
                change_points(username, points);
                delay(5000);
                break;
            }

            if (loser == 5)
            {
                change_color_rgb(20, 150, 40);
                clear_screen();
                printf("####      ## ##    ## ##   ### ###  ### ##\n");
                printf("##      ##   ##  ##   ##   ##  ##   ##  ##\n");
                printf("##      ##   ##  ####      ##       ##  ##\n");
                printf("##      ##   ##   #####    ## ##    ## ## \n");
                printf("##      ##   ##      ###   ##       ## ## \n");
                printf("##  ##  ##   ##  ##   ##   ##  ##   ##  ##\n");
                printf("### ###   ## ##    ## ##   ### ###  #### ##\n\n");
                reset_color();

                change_color_rgb(250, 200, 30);
                char a[100] = "YOU LOST LOSER. THE WORD WAS :";
                int b = strlen(a);
                for(int i = 0 ; i < b ; i++)
                {
                    printf("%c", a[i]);
                    delay(100);
                }

                for(int i = 0 ; i < tedad ; i++)
                {
                    printf("%c", word[i]);
                    delay(100);
                }
                reset_color();
                delay(5000);
                break;
            }
        }
    }
}

void loser_game2(char username[50], int points, char word[50], int tedad)
{
    char jakhali[50], estefade_shode[50];
    for (int i = 0; i < tedad; i++)
    {
        jakhali[i] = '-';
        printf("%c", jakhali[i]);
    }
    int check = 0, loser = 0, flag_kol = 0, estefade = 0, tedad_estefade = 0, check_estefade = 0;
    while (1)
    {
        check_estefade = 0;
        flag_kol = 0;
        check = 0;

        clear_screen();
        change_color_rgb(20, 150, 40);
        if (loser >= 2 && loser < 4)
        {
            printf("####\n");
            printf("##\n");
            printf("##\n");
            printf("##\n");
            printf("##\n");
            printf("##  ##\n");
            printf("### ###\n");
        }

        else if (loser >= 4 && loser < 6)
        {
            printf("####      ## ##\n");
            printf("##      ##   ##\n");
            printf("##      ##   ##\n");
            printf("##      ##   ##\n");
            printf("##      ##   ##\n");
            printf("##  ##  ##   ##\n");
            printf("### ###   ## ##\n");
        }

        else if (loser >= 6 && loser < 8)
        {
            printf("####      ## ##    ## ##\n");
            printf("##      ##   ##  ##   ##\n");
            printf("##      ##   ##  ####   \n");
            printf("##      ##   ##   ##### \n");
            printf("##      ##   ##      ###\n");
            printf("##  ##  ##   ##  ##   ##\n");
            printf("### ###   ## ##    ## ##\n");
        }

        else if (loser >= 8)
        {
            printf("####      ## ##    ## ##   ### ###\n");
            printf("##      ##   ##  ##   ##   ##  ## \n");
            printf("##      ##   ##  ####      ##     \n");
            printf("##      ##   ##   #####    ## ##  \n");
            printf("##      ##   ##      ###   ##     \n");
            printf("##  ##  ##   ##  ##   ##   ##  ## \n");
            printf("### ###   ## ##    ## ##   ### ###\n");
        }
        reset_color();

        change_color_rgb(250, 200, 30);
        for (int i = 0; i < tedad; i++)
        {
            printf("%c ", jakhali[i]);
        }

        reset_color();

        char t = getch();

        if (estefade == 0)
        {
            estefade_shode[tedad_estefade] = t;
            tedad_estefade++;
            estefade = 1;

            for (int i = 0; i < tedad; i++)
            {
                if (t == word[i])
                {
                    jakhali[i] = t;
                    check = 1;
                }
            }

            if (check == 0)
            {
                loser++;
            }
        }

        else if (estefade == 1)
        {
            for (int i = 0; i < tedad_estefade; i++)
            {
                if (estefade_shode[i] == t)
                {
                    change_color_rgb(250, 200, 30);
                    printf("\n\nyou have already used this letter. You have used this letters till now:");
                    for (int i = 0; i < tedad_estefade; i++)
                    {
                        printf(" %c,", estefade_shode[i]);
                    }
                    reset_color();
                    delay(3500);
                    check_estefade = 1;
                    break;
                }
            }

            if (check_estefade == 1)
            {
                continue;
            }

            else
            {
                estefade_shode[tedad_estefade] = t;
                tedad_estefade++;
            }

            for (int i = 0; i < tedad; i++)
            {
                if (t == word[i])
                {
                    jakhali[i] = t;
                    check = 1;
                }
            }

            if (check == 0)
            {
                loser++;
            }

            for (int i = 0; i < tedad; i++)
            {
                if (jakhali[i] == '-')
                {
                    flag_kol = 1;
                }
            }

            if (flag_kol == 0)
            {
                clear_screen();
                change_color_rgb(20, 150, 40);
                printf("##   ##    ####   ###  ##  ###  ##  ### ###  ### ##\n");
                printf("##   ##     ##      ## ##    ## ##   ##  ##   ##  ##\n");
                printf("##   ##     ##     # ## #   # ## #   ##       ##  ##\n");
                printf("## # ##     ##     ## ##    ## ##    ## ##    ## ## \n");
                printf("# ### #     ##     ##  ##   ##  ##   ##       ## ## \n");
                printf(" ## ##      ##     ##  ##   ##  ##   ##  ##   ##  ##\n");
                printf("##   ##    ####   ###  ##  ###  ##  ### ###  #### ##\n");
                reset_color();

                char a[100] = "YOU WON. CONGRATULATION. THE WORD WAS: ";
                int b = strlen(a);
                change_color_rgb(250, 200, 30);
                printf("\n");
                for (int i = 0; i < b; i++)
                {
                    printf("%c", a[i]);
                    delay(100);
                }

                for (int i = 0; i < tedad; i++)
                {
                    printf("%c", word[i]);
                    delay(100);
                }
                reset_color();

                change_points(username, points);
                delay(5000);
                break;
            }

            if (loser == 10)
            {
                change_color_rgb(20, 150, 40);
                clear_screen();
                printf("####      ## ##    ## ##   ### ###  ### ##\n");
                printf("##      ##   ##  ##   ##   ##  ##   ##  ##\n");
                printf("##      ##   ##  ####      ##       ##  ##\n");
                printf("##      ##   ##   #####    ## ##    ## ## \n");
                printf("##      ##   ##      ###   ##       ## ## \n");
                printf("##  ##  ##   ##  ##   ##   ##  ##   ##  ##\n");
                printf("### ###   ## ##    ## ##   ### ###  #### ##\n\n");
                reset_color();

                change_color_rgb(250, 200, 30);

                char a[100] = "YOU LOST LOSER. THE WORD WAS :";
                int b = strlen(a);

                for (int i = 0; i < b; i++)
                {
                    printf("%c", a[i]);
                    delay(100);
                }

                for (int i = 0; i < tedad; i++)
                {
                    printf("%c", word[i]);
                    delay(100);
                }
                delay(4000);
                break;
            }
        }
    }
}

void leaderBoard()
{
    char esm[100][100], temp_word[50];
    int emtiaz[50], tedad = 0, temp = 0, flag = 0, i = 0;

    FILE *file = fopen("leaderboard.txt", "r");
    if (file == NULL)
    {
        printf("please go to the sign up part.");
        delay(3000);
    }
    while (1)
    {
        while (fscanf(file, "%s%d", esm[i], &emtiaz[i]) != EOF)
        {
            i++;
            tedad++;
        }
        for (int i = 0; i < tedad; i++)
        {
            for (int j = 0; j < tedad - 1; j++)
            {
                if (emtiaz[j] < emtiaz[j + 1])
                {
                    temp = emtiaz[j];
                    emtiaz[j] = emtiaz[j + 1];
                    emtiaz[j + 1] = temp;

                    strcpy(temp_word, esm[j]);
                    strcpy(esm[j], esm[j + 1]);
                    strcpy(esm[j + 1], temp_word);
                }
            }
        }

        clear_screen();
        change_color_rgb(250, 200, 30);
        for (int i = 0; i < tedad; i++)
        {
            printf("%s   %d\n", esm[i], emtiaz[i]);
            // fprintf(file, "%s   %d\n", esm[i], esm[i]);
        }

        fclose(file);

        printf("\n\nIf you want to go to menu press ESC:");
        reset_color();
        char a = getch();
        if (a == 27)
        {
            break;
        }
    }
}

void change_password(char username[50], char password[50])
{
    FILE *file, *temp;
    file = fopen("names.txt", "r");
    temp = fopen("temp_names.txt", "w");

    char names[50];
    char temp_pass[50];

    while (!feof(file))
    {
        fscanf(file, "%s    %s\n", names, temp_pass);
        
        int m = strcmp(names, username);

        if (m == 0)
        {
            fprintf(temp, "%s   %s\n", names, password);
        }

        else
        {
            fprintf(temp, "%s   %s\n", names, temp_pass);
        }
    }

    fclose(file);
    fclose(temp);

    remove("names.txt");
    rename("temp_names.txt", "names.txt");
}
