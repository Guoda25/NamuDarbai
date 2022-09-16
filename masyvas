#include <iostream>
#include <string>
#include <iomanip>

struct duomenys {
    std::string Vard, Pav;
    int paz[10] = { 0 };
    int egz;
    float galut = 0;
};

void mediana(int pazymiai[]) // randa mediana
{
    int counter = 0;
    for (int i = 0; i < 10; i++)
    {
        if (pazymiai[i] > 0)
        {
            counter++;
        }
        if (pazymiai[i] == -1)
        {
            pazymiai[i] = 0;
            break;
        }
    }
    if (counter % 2 == 0) 
    {
        std::cout << float(((pazymiai[counter / 2 - 1]) + (pazymiai[(counter / 2)])) / 2.0);
    }
    else
    {
        std::cout << pazymiai[(counter / 2)];
    }
    std::cout << std::endl;
}

int random_paz() // generuoja random pazymius
{
    srand(time(NULL));
    return rand() % 10 + 1;
}

void automated (duomenys Eil[], int i, int paz_sk)
{
    Eil[i].egz = random_paz();
    for (int x = 0; x < paz_sk; x++)
    {
        Eil[i].paz[x] = random_paz();
    }
    Eil[i].galut = Eil[i].galut / paz_sk;
    Eil[i].galut = Eil[i].galut * 0.4 + 0.6 * Eil[i].egz;

}


void ranka (duomenys Eil[], int i) 
{
    do {
        std::cout << "Įveskite egzamino pažymį:\n";
        std::cin >> Eil[i].egz;
    } while (Eil[i].egz < 0 || Eil[i].egz > 10);
    std::cout << "Įveskite kitus pažymius (baigę, įveskite '-1'):";
    int counter = 0;
    do {
        std::cin >> Eil[i].paz[counter];
        if (Eil[i].paz[counter] != -1) { Eil[i].galut = Eil[i].galut + (float)Eil[i].paz[counter]; }
        counter++;
    } while (Eil[i].paz[counter - 1] != -1);
    counter--;
    Eil[i].galut = Eil[i].galut / counter;
    Eil[i].galut = Eil[i].galut * 0.4 + 0.6 * Eil[i].egz;
}
bool has_digit(std::string s)
{
    return (s.find_first_of("0123456789") != std::string::npos);
}

void vardas (duomenys Eil[], int i) 
{
    std::cout << "Įveskite studento nr. " << i + 1 << " duomenis:\n";
    do {
        std::cout << "Įveskite studento nr. " << i + 1 << " VARDĄ:\n";
        std::cin >> Eil[i].Vard;
    } while (Eil[i].Vard.length() < 0 || Eil[i].Vard.length() > 25 || has_digit(Eil[i].Vard));
    do {
        std::cout << "Įveskite studento nr. " << i + 1 << " PAVARDĘ:\n";
        std::cin >> Eil[i].Pav;
    } while (Eil[i].Pav.length() < 0 && Eil[i].Pav.length() > 25 || has_digit(Eil[i].Pav));
    std::cout << std::endl;
}

void rezultatai (duomenys Eil[], int studentu_sk) //atspausdina rezultatus
{
    std::cout << "\n\n";
    std::cout << std::setw(20) << std::left << "Vardas"
        << std::setw(20) << std::left << "Pavardė"
        << std::setw(18) << std::left << "Galutinis(vid.)/"
        << std::left << "Galutinis(med.)\n"
        << "--------------------------------------------------------------------------\n";
    for (int i = 0; i < studentu_sk; i++)
    {
        std::cout << std::setw(20) << std::left << Eil[i].Vard
            << std::setw(20) << std::left << Eil[i].Pav
            << std::setw(18) << std::left << Eil[i].galut;
        mediana(Eil[i].paz);
    }
    std::cout << "\n\n";
}

int main()
{
    int studentu_sk;
    char temp;
    do
    {
        std::cout << "Įveskite studentų kiekį:\n";
        std::cin >> studentu_sk;
    } 
      while (int(studentu_sk) < 0 || int(studentu_sk) > 255);
    duomenys Eil[25];
    do
    {
        std::cout << "Jeigu norite, kad studentų pažymiai būtų suvesti automatiškai - ĮVESKITE \"A\"\n Jeigu norite suvesti duomenis patys - ĮVESKITE \"N\"\n";
        std::cin >> temp;
        if (temp != 'a' && temp != 'A' && temp != 'n' && temp != 'N') { std::cout << "pakartokite, netinkamas simbolis\n"; }
    } while (temp != 'a' && temp != 'A' && temp != 'n' && temp != 'N');
    for (int i = 0; i < studentu_sk; i++)
    {
        vardas(Eil, i);
        if (temp == 'n' || temp == 'N') { ranka(Eil, i); }
        else { automated (Eil, i, 5); }
    }
    rezultatai(Eil, studentu_sk);
    system("pause");
    return 0;
}
