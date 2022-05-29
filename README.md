#include <iostream>

using namespace std;

int isiQueue[100];
const int maksimal = 100;
int jumlah = 0;
auto input_nilai = 0;

bool IsEmpty()
{
  return jumlah == 0;
}

bool IsFull()
{
  return jumlah >= maksimal;
}

void TambahAntrian()
{
  if (IsFull())
  {
    cout << "Antrian sudah penuh, silahkan kembali lagi nanti" << endl;
    return;
  }

  cout << "Silahkan ambil nomor antrian.....\n";
  jumlah += 1;
  isiQueue[jumlah] = input_nilai;
  cout << "Anda berada diantrian ke " << input_nilai + 1 << endl;
  input_nilai ++;
  cout << endl;

}

void PanggilAntrian()
{
  if (IsEmpty())
  {
    cout << "Antrian kosong!\n\n";
    return;
  }

  cout << "Nomor antrian ke " << isiQueue[1] + 1 << " dipanggil\n\n";
  for (auto i = 1; i <= jumlah; i++)
  {
    isiQueue[i] = isiQueue[i + 1];
  }

  jumlah -= 1;
}

void Print()
{
  if (IsEmpty())
  {
    cout << "Antrian masih kosong!\n\n";
    return;
  }

  cout << "Nomor yang sedang mengantri : ";
  for (auto i = 1; i <= jumlah; i++)
  {
    cout << "[" << isiQueue[i] + 1 << "] ";
  }
  cout << "\n\n";
}

int main()
{
  auto pilihan_user = 0;
  auto isLoop = true;

  while (isLoop)
  {
    cout << "Menu antrian"
         << "\n1. Tambah antrian"
         << "\n2. Cek antrian"
         << "\n3. Panggil"
         << "\n4. Keluar"<< endl;
    cout << "Masukan pilihan: ";
    cin >> pilihan_user;
    cout << endl;

    switch (pilihan_user)
    {
    case 1:
      TambahAntrian();
      break;

    case 2:
      Print();
      break;

    case 3:
      PanggilAntrian();
      break;

    case 4:
      cout << "Terima kasih!\n";
      isLoop = false;
      break;

    default:
      cout << "Salah input!" << endl;
      cout << endl;
      break;
    }
  }
  return 0;
}
