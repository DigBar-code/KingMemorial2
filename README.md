# KingMemorial2
As Ammended
. DNSPNM – Długość Najdłuższego Spójnego Podciągu Nierosnącego

int DNSPNM(int A[])
{
    // Długość Najdłuższego Spójnego Podciągu Niemalejącego
    int maks_dl = 1, akt_dl = 1, i;

    for (i = 1; i < N; i++)
    {
        if (A[i] >= A[i - 1])
        {
            akt_dl++;
            if (akt_dl > maks_dl)
                maks_dl = akt_dl;
        }
        else
        {
            akt_dl = 1;
        }
    }
    return maks_dl;
}


✅ 2. NSPNM – Indeks początku najdłuższego podciągu niemalejącego



int NSPNM(int A[], int *maks_dl)
{
    // Najdłuższy Spójny Podciąg Niemalejący
    int akt_dl = 1, maks_pocz = 0, i;

    *maks_dl = 1;

    for (i = 1; i < N; i++)
    {
        if (A[i] >= A[i - 1])
        {
            akt_dl++;
            if (akt_dl > *maks_dl)
            {
                *maks_dl = akt_dl;
                maks_pocz = i - akt_dl + 1;
            }
        }
        else
        {
            akt_dl = 1;
        }
    }
    return maks_pocz;
}




✅ 3. MSPS – Maksymalna Suma Podciągu Spójnego (prosta wersja O(N²))



int MSPS(int A[])
{
    int maks_suma = 0, akt_suma, i, j;

    for (i = 0; i < N; i++)
    {
        akt_suma = 0;
        for (j = i; j < N; j++)
        {
            akt_suma += A[j];
            if (akt_suma > maks_suma)
                maks_suma = akt_suma;
        }
    }
    return maks_suma;
}




✅ 4. PSMS – Podciąg Spójny o Maksymalnej Sumi (Kadane + indeks)



void PSMS(int A[], int *maks_suma, int *maks_pocz)
{
    *maks_suma = 0;
    *maks_pocz = 0;

    int akt_suma = 0, akt_pocz = 0, i;

    for (i = 0; i < N; i++)
    {
        if (akt_suma + A[i] > 0)
        {
            akt_suma += A[i];
            if (akt_suma > *maks_suma)
            {
                *maks_suma = akt_suma;
                *maks_pocz = akt_pocz;
            }
        }
        else
        {
            akt_suma = 0;
            akt_pocz = i + 1;
        }
    }
}




Jeśli chcesz, mogę:


✅ przepisać cały kod w wersji „książkowej” z main()

✅ napisać wersję ulepszoną/nowoczesną

✅ zrobić jedną bibliotekę z tymi funkcjami

✅ dodać komentarze, przykłady wejścia/wyjścia, testy


Powiedz tylko, czego potrzebujesz.



void Losuj(int A[], int min, int max)
{
    for (int i = 0; i < N; i++)
        A[i] = rand() % (max - min + 1) + min;
}

Losuj(A, -50, 50);








ChatGPT może popełniać błędy. Sprawdź ważne informacje. 
