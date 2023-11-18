#include <stdio.h>
#include <string.h>

#define SIZE 1000

void Search_Text(const char* Main_Text, const char* Searched_Text)
{
	int Main_Text_Length = strlen(Main_Text);
	int Searched_Text_Length = strlen(Searched_Text);

	for (int i = 0; i <= (Main_Text_Length - Searched_Text_Length); i++)
	{
		int flag = 1;

		for (int j = 0; j < Searched_Text_Length; j++)
		{
			if (Main_Text[i + j] != Searched_Text[j])
			{
				flag = 0;
				break;
			}
		}

		if (flag)
		{
			for (int k = 0; k < Main_Text_Length; k++)
			{
				if (k >= i && k < i + Searched_Text_Length)
				{
					printf("\033[1;31m%c\033[0m", Main_Text[k]);
				}
				else {
					printf("%c", Main_Text[k]);
				}
			}

			printf("\n\nThe searched text is found in the main text.\n");
			return;
		}
	}

	printf("\n\nThe searched text is not found in the main text.\n");
}
int main(void) {
	char Main_Text[SIZE];
	printf("Enter Main Text: ");
	fgets(Main_Text, sizeof(Main_Text), stdin);
	Main_Text[strcspn(Main_Text, "\n")] = '\0';

	char Searched_Text[SIZE];
	printf("Enter Searched Text:");
	fgets(Searched_Text, sizeof(Searched_Text), stdin);
	Searched_Text[strcspn(Searched_Text, "\n")] = '\0';

	printf("\n");
	Search_Text(Main_Text, Searched_Text);

	return 0;
}


