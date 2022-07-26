###### Nama : Dimas Fadhillah R
###### Kelas : XII RPL1
###### No Absen:21

# Modul 1

1. Lakukan proses instalasi framework laravel kedalam folder dengan nama masing-masing.
2. Buatlah projek pertama laravel dengan nama projek “penjualan” dan tampilkan dalam browser.

```
composer create-project laravel/laravel penjualan
```


# Modul 2
1. Buatlah migration tabel kategori dengan menggunakan teknik yang telah di pelajari dalamodul ini.
2. Berikan data dengan menggunakan seeder yang telah anda pelajari pada modul ini.

Soal Nomer 1

###### Langkah Pertama
```
php artisan make:migration create_kategori_table>
```

###### Langkah Kedua
Isikan kode di bawah ini kedalam file yang dibuat
```
<?php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

return new class extends Migration
{
    /**
     * Run the migrations.
     *
     * @return void
     */
    public function up()
    {
        Schema::create('kategori', function (Blueprint $table) {
            $table->id();
            $table->string('name');
            $table->timestamps();
        });
    }

    /**
     * Reverse the migrations.
     *
     * @return void
     */
    public function down()
    {
        Schema::dropIfExists('kategori');
    }
};
```

Langkah ke 3

Untuk mengeksekusinya, jalankan perintah berikut
```
php artisan migrate
```
Langkah ke 4

Setelah itu kita melanjutkan untuk membuat model kita harus menjalankan printah artisan dengan script sebagai berikut:

```
php artisan make:model Kategori
```

Isi kode di bawah ke dalam file
```
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;

class Kategori extends Model
{
    use HasFactory;

    protected $table = 'kategori';
}
```

## Soal ke 2

Langkah ke 1

Pembuatan Seeder
Untuk membuat seeder gunakan artisan berikut pada cmd pada VS Code
```
php artisan make:seeder kategoriTableSeeder
```
Selanjutnya buka file kategoriTableSeeder yang telah dibuat dan tambahkan script pada method
run() sehingga menjadi seperti berikut:
```
<?php

namespace Database\Seeders;

use Illuminate\Database\Console\Seeds\WithoutModelEvents;
use Illuminate\Database\Seeder;
use DB;

class kategoriTableSeeder extends Seeder
{
    /**
     * Run the database seeds.
     *
     * @return void
     */
    public function run()
    {
        DB::table('kategori')->insert(array(
            [
                'name' => 'Perlengkapan Sekolah',
            ],
            [   
                'name' => 'Komputer',
            ],
            [   
                'name' => 'Sabun',
            ],
            [   
                'name' => 'Accesories',
            ],
            [   
                'name' => 'ATK',
            ]
        ));
    }
}
```
Langkah ke 2

Buka file bagian data base dan isi code bagian public function run()
```
$this->call(kategoriTableSeeder::class);
```
dengan tujuan untuk memanggil class bagian kategoriTableSeeder untuk berfungsi pada DatabaseSeeder.

Langkah ke 3

Sekarang kita dapat menjalankan perintah atisan pada cmd untuk Menjalankan seeder yang
telah dibaut dengan perintah sebagai berikut:
```
php artisan db:seed
```




