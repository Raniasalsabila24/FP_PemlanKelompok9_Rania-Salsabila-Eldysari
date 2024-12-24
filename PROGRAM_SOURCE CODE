#include <stdio.h>
#include <string.h>
#include <math.h>

// Fungsi untuk menampilkan daftar makanan
void tampilkanMenu(char menu[][50], int n) {
    printf("\nDaftar Makanan:\n");
    for (int i = 0; i < n; i++) {
        printf("%d. %s\n", i + 1, menu[i]);
    }
}

// Fungsi Bubble Sort untuk mengurutkan menu
void bubbleSort(char menu[][50], int n) {
    char temp[50];
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (strcmp(menu[j], menu[j + 1]) > 0) {
                strcpy(temp, menu[j]);
                strcpy(menu[j], menu[j + 1]);
                strcpy(menu[j + 1], temp);
            }
        }
    }
}

// Fungsi Jump Search untuk mencari makanan
int jumpSearch(char menu[][50], int n, char target[]) {
    int step = sqrt(n);
    int prev = 0;

    while (strcmp(menu[fmin(step, n) - 1], target) < 0) {
        prev = step;
        step += sqrt(n);
        if (prev >= n) return -1;
    }

    for (int i = prev; i < fmin(step, n); i++) {
        if (strcmp(menu[i], target) == 0) return i;
    }

    return -1;
}

int main() {
    int n;
    char target[50];

    // Input jumlah makanan
    printf("Masukkan jumlah makanan favorit: ");
    scanf("%d", &n);
    getchar(); // Menghilangkan newline dari buffer

    char menu[n][50];

    // Input nama makanan
    for (int i = 0; i < n; i++) {
        printf("Masukkan nama makanan ke-%d: ", i + 1);
        fgets(menu[i], sizeof(menu[i]), stdin);
        menu[i][strcspn(menu[i], "\n")] = '\0'; // Menghapus newline
    }

    // Menampilkan menu sebelum pengurutan
    tampilkanMenu(menu, n);

    // Mengurutkan makanan menggunakan Bubble Sort
    bubbleSort(menu, n);

    // Menampilkan menu setelah pengurutan
    printf("\nDaftar makanan setelah diurutkan:\n");
    tampilkanMenu(menu, n);

    // Pencarian makanan menggunakan Jump Search
    printf("\nMasukkan nama makanan yang ingin dicari: ");
    fgets(target, sizeof(target), stdin);
    target[strcspn(target, "\n")] = '\0'; // Menghapus newline

    int index = jumpSearch(menu, n, target);

    // Output hasil pencarian
    if (index != -1) {
        printf("Makanan '%s' ditemukan pada indeks ke-%d (urutan ke-%d).\n", target, index, index + 1);
    } else {
        printf("Makanan '%s' tidak ditemukan dalam daftar.\n", target);
    }

    return 0;
}
