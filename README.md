# Tutorial File Handling di C

---

# 1. Membuka & Menutup File

### Fungsi:
- `fopen()`
- `fclose()`

### Contoh:

```c
FILE *fp = fopen("data.txt", "r");   // membuka file untuk dibaca

if (fp == NULL) {
    printf("File tidak ditemukan\n");
    return 0;
}

printf("File berhasil dibuka!\n");

fclose(fp);    // menutup file
```

### Mode `fopen()`:

| Mode | Arti |
|------|------|
| "r" | read (file harus ada) |
| "w" | write (buat file baru, hapus isi lama) |
| "a" | append (tulis di akhir file) |
| "r+" | read + write |
| "w+" | read + write (overwrite file) |
| "a+" | read + write (mulai dari akhir file) |

---

# 2. Membaca Karakter per Karakter (`fgetc`)

```c
FILE *fp = fopen("data.txt", "r");

char c;
while ((c = fgetc(fp)) != EOF) {
    printf("%c", c);
}

fclose(fp);
```

---

# 3. Menulis Karakter ke File (`fputc`)

```c
FILE *fp = fopen("output.txt", "w");

fputc('A', fp);
fputc('\n', fp);
fputc('Z', fp);

fclose(fp);
```

---

# 4. Membaca Satu Baris (`fgets`)

```c
FILE *fp = fopen("data.txt", "r");

char buffer[100];

while (fgets(buffer, sizeof(buffer), fp)) {
    printf("Baris: %s", buffer);
}

fclose(fp);
```

---

# 5. Menulis Satu Baris (`fputs`)

```c
FILE *fp = fopen("output.txt", "w");

fputs("Halo dunia!\n", fp);
fputs("Belajar file handling.", fp);

fclose(fp);
```

---

# 6. Membaca Data Terformat (`fscanf`)

```c
FILE *fp = fopen("data.txt", "r");

int age;
char name[50];

fscanf(fp, "%d %s", &age, name);

printf("Nama: %s, Umur: %d\n", name, age);

fclose(fp);
```

---

# 7. Menulis Data Terformat (`fprintf`)

```c
FILE *fp = fopen("output.txt", "w");

int age = 21;
char name[] = "Lili";

fprintf(fp, "Nama: %s, Umur: %d\n", name, age);

fclose(fp);
```

---

# 8. Membaca File Binary (`fread`)

```c
struct Data {
    int id;
    float nilai;
};

FILE *fp = fopen("data.bin", "rb");

struct Data d;

fread(&d, sizeof(struct Data), 1, fp);

printf("ID: %d, Nilai: %.2f\n", d.id, d.nilai);

fclose(fp);
```

---

# 9. Menulis File Binary (`fwrite`)

```c
struct Data {
    int id;
    float nilai;
};

struct Data d = {101, 95.5};

FILE *fp = fopen("data.bin", "wb");

fwrite(&d, sizeof(struct Data), 1, fp);

fclose(fp);
```

---

# 10. Demo Lengkap: Copy File Baris per Baris

```c
FILE *in = fopen("input.txt", "r");
FILE *out = fopen("output.txt", "w");

char line[200];

while (fgets(line, sizeof(line), in)) {
    fprintf(out, "Copy: %s", line);
}

fclose(in);
fclose(out);
```

---

# Ringkasan Singkat Per Fungsi

| Fungsi | Keterangan |
|--------|------------|
| fgetc() | baca 1 karakter |
| fputc() | tulis 1 karakter |
| fgets() | baca 1 baris |
| fputs() | tulis 1 baris |
| fscanf() | baca data terformat |
| fprintf() | tulis data terformat |
| fread() | baca binary (block data) |
| fwrite() | tulis binary |

---

# Selesai!
