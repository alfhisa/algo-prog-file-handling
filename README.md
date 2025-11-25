# Tutorial File Handling di C

---

# 1. Membuka & Menutup File (`fopen`, `fclose`)
**`fopen()` membuka file, `fclose()` menutup file.**

```c
#include <stdio.h>

int main() {
    FILE *fp = fopen("data.txt", "r");   // membuka file untuk dibaca

    if (fp == NULL) {
        printf("File tidak ditemukan
");
        return 0;
    }

    printf("File berhasil dibuka!
");

    fclose(fp);    // menutup file
    return 0;
}
```

---

# 2. Membaca Karakter per Karakter (`fgetc`)
**`fgetc()` membaca 1 karakter dari file.**

```c
#include <stdio.h>

int main() {
    FILE *fp = fopen("data.txt", "r");
    if (!fp) return 0;

    int c;
    while ((c = fgetc(fp)) != EOF) {
        putchar(c);
    }

    fclose(fp);
    return 0;
}
```

---

# 3. Menulis Karakter per Karakter (`fputc`)
**`fputc()` menulis 1 karakter ke file.**

```c
#include <stdio.h>

int main() {
    FILE *fp = fopen("output.txt", "w");
    if (!fp) return 0;

    fputc('A', fp);
    fputc('\n', fp);
    fputc('Z', fp);

    fclose(fp);
    return 0;
}
```

---

# 4. Membaca Satu Baris (`fgets`)
**`fgets()` membaca 1 baris string dari file.**

```c
#include <stdio.h>

int main() {
    FILE *fp = fopen("data.txt", "r");
    if (!fp) return 0;

    char buffer[100];

    while (fgets(buffer, sizeof(buffer), fp)) {
        printf("Baris: %s", buffer);
    }

    fclose(fp);
    return 0;
}
```

---

# 5. Menulis Satu Baris (`fputs`)
**`fputs()` menulis string (tanpa format) ke file.**

```c
#include <stdio.h>

int main() {
    FILE *fp = fopen("output.txt", "w");
    if (!fp) return 0;

    fputs("Halo dunia!\n", fp);
    fputs("Belajar file handling.\n", fp);

    fclose(fp);
    return 0;
}
```

---

# 6. Membaca Data Terformat (`fscanf`)
**`fscanf()` membaca data sesuai format seperti integer, string, float, dll.**

```c
#include <stdio.h>

int main() {
    FILE *fp = fopen("data.txt", "r");
    if (!fp) return 0;

    int age;
    char name[50];

    fscanf(fp, "%d %s", &age, name);

    printf("Nama: %s, Umur: %d\n", name, age);

    fclose(fp);
    return 0;
}
```

---

# 7. Menulis Data Terformat (`fprintf`)
**`fprintf()` menulis data dengan format ke file.**

```c
#include <stdio.h>

int main() {
    FILE *fp = fopen("output.txt", "w");
    if (!fp) return 0;

    int age = 21;
    char name[] = "Lili";

    fprintf(fp, "Nama: %s, Umur: %d\n", name, age);

    fclose(fp);
    return 0;
}
```

---

# 8. Membaca File Binary (`fread`)
**`fread()` membaca data biner dalam bentuk blok (struct, array, dll).**

```c
#include <stdio.h>

struct Data {
    int id;
    float nilai;
};

int main() {
    FILE *fp = fopen("data.bin", "rb");
    if (!fp) return 0;

    struct Data d;

    fread(&d, sizeof(struct Data), 1, fp);

    printf("ID: %d\nNilai: %.2f\n", d.id, d.nilai);

    fclose(fp);
    return 0;
}
```

---

# 9. Menulis File Binary (`fwrite`)
**`fwrite()` menulis data biner ke file. Biasanya untuk struct.**

```c
#include <stdio.h>

struct Data {
    int id;
    float nilai;
};

int main() {
    struct Data d = {101, 95.5};

    FILE *fp = fopen("data.bin", "wb");
    if (!fp) return 0;

    fwrite(&d, sizeof(struct Data), 1, fp);

    fclose(fp);
    return 0;
}
```

---

# 10. Demo Copy File Baris per Baris
**Gabungan: `fgets()` → `fprintf()` untuk copy isi file.**

```c
#include <stdio.h>

int main() {
    FILE *in = fopen("input.txt", "r");
    FILE *out = fopen("output.txt", "w");

    if (!in || !out) return 0;

    char line[200];

    while (fgets(line, sizeof(line), in)) {
        fprintf(out, "Copy: %s", line);
    }

    fclose(in);
    fclose(out);

    return 0;
}
```

---

# Ringkasan Fungsi

| Fungsi | Keterangan |
|--------|------------|
| `fgetc()` | baca 1 karakter |
| `fputc()` | tulis 1 karakter |
| `fgets()` | baca 1 baris |
| `fputs()` | tulis string |
| `fscanf()` | baca data terformat |
| `fprintf()` | tulis data terformat |
| `fread()` | baca binary |
| `fwrite()` | tulis binary |

---

# Selesai!

