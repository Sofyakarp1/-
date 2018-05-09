# -
Первоначальный вариант
#include "stdafx.h"
#include <iostream>
#include <string>
#include <clocale>
#include <fstream>
#include <conio.h>
#include <map>
#include <vector>
#include <cstdlib>
#include <ctime>


char user_menu();
char menu_of_editing(std::string a);
void Texts(const char *PATH);
void Karta(int i, int n);
void Prize(int m, int f);
bool Free(int b, int array[], int  n);
void Pokupka(int array[], int f1, int f2, int n, int k);
void ShowPrize(int w, int f1, int f2, int n);

int main(int argc, char* argv[])
{
	setlocale(LC_ALL, "rus");
	int q, w, sum = 0, t, p;        /*q = ряд; w = место; t,p = пеменные для do, switch*/
	char answer = 0, item = 0;
	do
	{
		answer = user_menu();
		switch (answer) {
		case 49:
			do {
				item = menu_of_editing("\nЮНОНА И АВОСЬ");
				switch (item) {
				case 49:
					std::cout << "\n\n1. Найти подходящий билет по критериям" << std::endl;
					break;
				case 50:
				{
					std::cout << "2. Посмотреть карту мест и купить билет " << std::endl;
					Karta(5, 14);
					ShowPrize( 14, 1500, 1200, 4);
					int arr[] = { 2, 5, 7, 9 };
					Pokupka(arr, 1500, 1200, 4, 14);
				}
				system("pause");
				break;
				case 51:
					std::cout << "3. Посмотреть актеров премьеры" << std::endl;
					Texts("C:\\Myproject\\actUnona.txt");
					system("pause");
					break;
				case 52:
					std::cout << "4. Прочитать статью о выбранном спектакле" << std::endl;
					Texts("C:\\Myproject\\Unona.txt");
					system("pause");
					break;
				default:
					std::cout << std::endl;
					break;
				}
			} while (item != 48);
			item = 0;
			break;
		case 50:
			do {
				item = menu_of_editing("\nПЕР ГЮНТ. ");
				switch (item) {
				case 49:
					std::cout << "1. Найти подходящий билет по критериям" << std::endl;
					break;
				case 50:
				{
					std::cout << "2. Посмотреть карту мест и купить билет " << std::endl;
					Karta(6, 14);
					ShowPrize(14, 2000, 1800, 6);
					int arr[] = {4, 6, 12, 14, 13};
					Pokupka(arr, 2000, 1800, 5, 14);
				}
				system("pause");
				break;
				case 51:
					std::cout << "3. Посмотреть актеров премьеры" << std::endl;
					Texts("C:\\Myproject\\actPer.txt");
					system("pause");
					break;
				case 52:
					std::cout << "4. Прочитать статью о выбранном спектакле" << std::endl;
					Texts("C:\\Myproject\\Per.txt");
					system("pause");
					break;
				default:
					std::cout << std::endl;
					break;
				}
			} while (item != 48);
			item = 0;
			break;
		case 51:
			do {
				item = menu_of_editing("\nВИШНЕВЫЙ САД");
				switch (item) {
				case 49:
					std::cout << "\n\n1. Найти подходящий билет по критериям" << std::endl;
					break;
				case 50:
				{
					std::cout << "2. Посмотреть карту мест и купить билет " << std::endl;
					Karta(3, 12);
					ShowPrize(12, 1000, 750, 3);
					int arr[] = { 3, 4, 5, 11 };
					Pokupka(arr, 1000, 750, 3, 12);
				}
				system("pause");
				break;
				case 51:
					std::cout << "3. Посмотреть актеров премьеры" << std::endl;
					Texts("C:\\Myproject\\actVish.txt");
					system("pause");
					break;
				case 52:
					std::cout << "4. Прочитать статью о выбранном спектакле" << std::endl;
					Texts("C:\\Myproject\\Vish.txt");
					system("pause");
					break;
				default:
					std::cout << std::endl;
					break;
				}
			} while (item != 48);
			item = 0;
			break;
		case 52:
			do {
				item = menu_of_editing("\nЖЕНИТЬБА. ");
				switch (item) {
				case 49:
					std::cout << "1. Найти подходящий билет по критериям" << std::endl;
					break;
				case 50:
				{
					std::cout << "2. Посмотреть карту мест и купить билет " << std::endl;
					Karta(4, 16);
					ShowPrize(16, 2200, 1500, 4);
					int arr[] = { 1, 3, 5, 6, 7, 8, 13};
					Pokupka(arr, 2000, 1800, 4, 16);
				}
				system("pause");
				break;
				case 51:
					std::cout << "3. Посмотреть актеров премьеры" << std::endl;
					Texts("C:\\Myproject\\actGen.txt");
					system("pause");
					break;
				case 52:
					std::cout << "4. Прочитать статью о выбранном спектакле" << std::endl;
					Texts("C:\\Myproject\\Gen.txt");
					system("pause");
					break;
				default:
					std::cout << std::endl;
					break;
				}
			} while (item != 48);
			item = 0;
			break;


		default:
			break;
		}
	} while (answer != 48);
	return 0;

}



char user_menu()     //начальное меню 
{
	system("cls");
	std::string menu[] = { "\n       Список спектаклей, доступных для посещения:",
		"1. Юнона и Авось ", "2. Пер Гюнт",
		"3. Вишневый сад",
		"4. Женитьба",
		"0. Выход из программы" };
	const int size_arr = sizeof(menu) / sizeof(std::string);
	for (int i = 0; i < size_arr; i++) {
		std::cout << menu[i] << std::endl;
	}
	std::cout << std::endl << "Выберите действие: ";
	char answer = 0;
	std::cin >> answer;
	return answer;
}



char menu_of_editing(std::string a) { //меню редактирования
	system("cls");
	std::cout << a << std::endl;
	std::string menu[] = { "\n1. Найти подходящий билет по критериям",
		"2. Посмотреть карту мест и купить билет",
		"3. Посмотреть актеров премьеры",
		"4. Прочитать статью о выбранном спектакле",
		"0. Вернуться к списку спектаклей" };
	const int size_arr = sizeof(menu) / sizeof(std::string);
	for (int i = 0; i < size_arr; i++) {
		std::cout << menu[i] << std::endl;
	}
	std::cout << std::endl << "Выберите действие: ";
	char answer = 0;
	std::cin >> answer;
	return answer;
}



void Texts(const char *PATH) //печать из файла
{
	const int MAXLEN_STR = 256;
	const int ROW_COUNT = 100;
	//const char *PATH = "C:\\Myproject\\play.txt";
	char S[ROW_COUNT][MAXLEN_STR];
	int str_num = 0;
	std::ifstream in(PATH);
	while (!in.eof())
	{
		in.getline(S[str_num++], MAXLEN_STR);
	}
	if (!in.eof())
	{
		std::cout << "Invalid input" << std::endl;
	}
	in.close();
	for (int i = 0; i<str_num; i++)
	{
		std::cout << S[i] << '\n';
	}
	std::cin.get();
}

void Karta(int i, int n)      //Карта возможных мест ; i = рядов; n =  мест
{
	int k = 1, t = 1;
	std::vector<int>m(n);
	std::cout << "Ряд         Места \n\n";
	while (t != i)
	{

		std::cout << t << "   ";
		for (int j = 0; j< m.size(); j++)
		{
			std::cout << m[j] + k << " ";
			k++;
		}
		t++;
		k = 1;
		std::cout << "\n";

	}
}

void Prize(int m, int f)                 //Цены за билет и вывод из на экран     m = количсетво мест   f = начальаня цена 
{
	std::map <int, int> gquiz1;
	for (int s = 0; s< m + 1; s++)
	{
		gquiz1.insert(std::pair <int, int>(s, f));
	}
	//Выводим на экран 
	std::map <int, int> ::iterator itr;
	std::cout << "\n Цена за билеты  \n";
	std::cout << "\tМесто \t Цена  \n";
	for (itr = gquiz1.begin(); itr != gquiz1.end(); ++itr)
	{
		std::cout << '\t' << itr->first
			<< '\t' << itr->second << '\n';
	}
	std::cout << std::endl;
	std::cout << "Выберите место ";
}

bool Free(int b, int  array[], int  n) //Сводные места 
{
	int i, k = 0;
	for (i = 0; i<n; i++)
	{
		if (b == array[i])
			k++;
	}
	if (k>0)
		return false;
	else
		return true;

}

void Pokupka(int array[], int f1, int f2, int n, int k) // Покупаем билет 
{
	int i;
	int sum = 0, q, w;
	do {
		std::cout << "Для покупки билета введите ряд и место\n";
		std::cout << "Ряд = ";
		std::cin >> q;
		std::cout << "       Место = ";
		std::cin >> w;
		if (q > n | q < 0 | w < 0 | w>k)
		{
			std::cout << "Неверные даннные, попробуйте еще раз.";
		}
		else
		{
			if (Free(w, array, q))
			{
				std::cout << "        Место свободно!";
				if (q > 2)
				{
					sum = sum + f2;
					std::cout << "\nсумма = " << sum;
				}
				else
				{
					sum = sum + f1;
					std::cout << "\nсумма = " << sum;
				}
			}
			else std::cout << "        Место уже занято :( ";
		}
		std::cout << "\n\n1. Для продолжения покупки\n0. Для выхода в меню " << std::endl;
		std::cin >> i;
	} while (i!= 0);

}

void ShowPrize(int w, int f1, int f2, int n) // Цены за билеты 
{
	
	int q, t;
	do
	{
	std::cout << "Выберите ряд\n    ряд= ";
	std::cin >> q;
	if (q > n || q <= 0)
	{
		std::cout << "Такого ряда нет. Поробуйте еще раз..." << std::endl;
	}
	else {
		if (q == 1 || q == 2)
			Prize(w, f1);
		else
			Prize(w, f2);
	}
	std::cout << "\n\n0. Вернуться к просмотру\n1. Купить билет" << std::endl;
	std::cin >> t;
	} while (t != 1);
		//system("pause");
