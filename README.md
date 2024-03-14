```sh
# projek-pointer

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_LENGTH 2024
#define MIN_LENGTH 1945

void lessThanRequired(int *lengthOfText) {
    printf("The length of your text is less than specified, please update your text\n");
    *lengthOfText = MIN_LENGTH;
}

void equalThanRequired() {
    printf("Thank you, Your text length is correct\n");
}

void moreThanRequired(int *lengthOfText) {
    printf("Your text is too long, please reduce the text\n");
    *lengthOfText = MIN_LENGTH;
}

int checkLengthRequirement(char* text) {
    int length = strlen(text);
    if (length < MIN_LENGTH)
        return 0;
    else if (length == MIN_LENGTH)
        return 1;
    else
        return 2;
}

int main() {
    int lengthOfText, selectOption;
    FILE *fptr = NULL;
    char text[MAX_LENGTH];

    fptr = fopen("file.txt", "r");

    if (fptr == NULL) {
        printf("Error");
        exit(1);
    }

    fgets(text, MAX_LENGTH, fptr);

    fclose(fptr);

    selectOption = checkLengthRequirement(text);
    
    void (*options[3])(int *) = {lessThanRequired, equalThanRequired, moreThanRequired};
    options[selectOption](&lengthOfText);

    printf("\nThe Length is updated to %d", lengthOfText);

    return 0;
}
```
# PENJELAASAN
```sh
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
```
- Baris ini adalah untuk menyertakan header file standar C yang diperlukan untuk fungsi-fungsi standar seperti operasi input-output, alokasi memori dinamis, dan manipulasi string.

```sh
#define MAX_LENGTH 2024
#define MIN_LENGTH 1945
```
- Ini mendefinisikan dua konstanta: `MAX_LENGTH` yang menyatakan panjang maksimum teks yang diizinkan, dan `MIN_LENGTH` yang menyatakan panjang minimum yang diharapkan.

```sh
void lessThanRequired(int *lengthOfText) {
    printf("The length of your text is less than specified, please update your text\n");
    *lengthOfText = MIN_LENGTH;
```
Ini adalah sebuah fungsi yang dicetak pesan kesalahan jika panjang teks kurang dari yang diharapkan, dan kemudian memperbarui panjang teks menjadi nilai minimum yang diharapkan

  ```sh
  void equalThanRequired() {
    printf("Thank you, Your text length is correct\n");
````
- Ini adalah sebuah fungsi yang mencetak pesan jika panjang teks sama dengan yang diharapkan.

```sh
void moreThanRequired(int *lengthOfText) {
    printf("Your text is too long, please reduce the text\n");
    *lengthOfText = MIN_LENGTH;
```
-  Ini adalah sebuah fungsi yang mencetak pesan kesalahan jika panjang teks lebih dari yang diharapkan, dan kemudian memperbarui panjang teks menjadi nilai minimum yang diharapkan.
```sh
int checkLengthRequirement(char* text) {
    int length = strlen(text);
    if (length < MIN_LENGTH)
        return 0;
    else if (length == MIN_LENGTH)
        return 1;
    else
        return 2;
}
```
- Ini adalah fungsi yang memeriksa panjang teks dan mengembalikan nilai sesuai dengan kondisi panjangnya. 0 jika kurang dari yang diharapkan, 1 jika sama, dan 2 jika lebih dari yang diharapkan.

```sh
int main() {
    int lengthOfText, selectOption;
    FILE *fptr = NULL;
    char text[MAX_LENGTH];

    fptr = fopen("file.txt", "r");

    if (fptr == NULL) {
        printf("Error");
        exit(1);
    }
```
- Di dalam fungsi main, variabel lokal dideklarasikan untuk menyimpan panjang teks (lengthOfText), pilihan opsi (selectOption), dan file pointer (fptr). File `"file.txt"` dibuka untuk dibaca, dan jika pembukaan gagal, pesan kesalahan dicetak dan program keluar.

```sh
    fgets(text, MAX_LENGTH, fptr);

    fclose(fptr);

    selectOption = checkLengthRequirement(text);
```
- Teks dibaca dari file menggunakan fgets dan disimpan di dalam array text. File pointer ditutup setelah pembacaan selesai. Kemudian, fungsi `checkLengthRequirement` dipanggil untuk memeriksa panjang teks dan hasilnya disimpan di dalam selectOptio

```sh
    void (*options[3])(int *) = {lessThanRequired, equalThanRequired, moreThanRequired};
    options[selectOption](&lengthOfText);
```
- ni mendeklarasikan array dari pointer fungsi void yang mengambil satu parameter bertipe int pointer. Array ini diisi dengan alamat dari fungsi-fungsi yang sesuai dengan pilihan panjang teks. Fungsi yang sesuai kemudian dipanggil dengan memberikan alamat variabel `lengthOfText` sebagai argumen.

```sh
   printf("\nThe Length is updated to %d", lengthOfText);

   return 0;
```
- Akhirnya, panjang teks yang telah diperbarui (jika perlu) dicetak, dan program selesai dengan mengembalikan 0.

# OUTPUT
![alt text](?raw=true)
