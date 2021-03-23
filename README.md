package Java;
import java.util.Scanner;
public class tugas3 {
    public static void main(String[] args) {
        // PinjamOnline [] akun = new PinjamOnline[4];
        // akun[0] = new PinjamOnline("Ana");
        // akun[1] = new PinjamOnline("Doni");
        // akun[2] = new PinjamOnline("Ikhsan");
        // akun[3] = new PinjamOnline("Adi");
        // akun[0].pinjam();
        // akun[1].pinjam();
        // akun[2].pinjam();
        // akun[2].kembalikan();
        // akun[0].kembalikan();
        // akun[3].pinjam();
        // akun[3].kembalikan();
        // akun[2].pinjam();
        // akun[1].pinjam();
        // akun[1].kembalikan();
        // akun[2].kembalikan();
        // akun[1].pinjam();
        // for(int i = 0;i < 4;i++) {
        //     System.out.println("Nama : "+akun[i].nama);
        //     System.out.println("Lama peminjaman : "+akun[i].getLamaPeminjaman()+" hari");
        //     System.out.println("Nominal pinjaman : Rp"+akun[i].getPinjaman()+"\n");
        // }
        // System.out.println("Sisa saldo : Rp"+akun[3].getSaldoSistem());

        // PinjamOnline [] akun = new PinjamOnline[3];
        // akun[0] = new PinjamOnline("Tia");
        // akun[1] = new PinjamOnline("Fira");
        // akun[2] = new PinjamOnline("Ani");
        // akun[0].pinjam();
        // akun[1].kembalikan();
        // akun[1].pinjam();
        // akun[0].kembalikan();
        // akun[2].pinjam();
        // akun[0].kembalikan();
        // for(int i = 0;i < 3;i++) {
        //     System.out.println("Nama : "+akun[i].nama);
        //     System.out.println("Lama peminjaman : "+akun[i].getLamaPeminjaman()+" hari");
        //     System.out.println("Nominal pinjaman : Rp"+akun[i].getPinjaman()+"\n");
        // }
        // System.out.println("Sisa saldo : Rp"+akun[2].getSaldoSistem());

        // PinjamOnline [] akun  = new PinjamOnline[3];
        // akun[0] = new PinjamOnline("Dani");
        // akun[1] = new PinjamOnline("Bagus");
        // akun[2] = new PinjamOnline("Vania");
        // akun[0].pinjam();
        // akun[1].pinjam();
        // akun[1].kembalikan();
        // akun[0].kembalikan();
        // akun[2].pinjam();
        // akun[1].pinjam();
        // akun[0].kembalikan();
        // akun[2].pinjam();
        // for(int i = 0;i < 3;i++) {
        //     System.out.println("Nama : "+akun[i].nama);
        //     System.out.println("Lama peminjaman : "+akun[i].getLamaPeminjaman()+" hari");
        //     System.out.println("Nominal pinjaman : Rp"+akun[i].getPinjaman()+"\n");
        // }
        // System.out.println("Sisa saldo : Rp"+akun[2].getSaldoSistem());
    }
}

class PinjamOnline {
    Scanner inp = new Scanner(System.in);
    private static double saldoSistem = 5000000;
    private double pinjaman;
    String nama;
    private int lamaPeminjaman;
    double denda = 0;

    PinjamOnline(String nama) {
        this.nama = nama;
    }

    public double getSaldoSistem() {
        return saldoSistem;
    }

    public void setSaldoSistem(double saldoSistem) {
        PinjamOnline.saldoSistem = saldoSistem;
    }

    public void setPinjaman(double Pinjaman) {
        pinjaman = Pinjaman;
    }

    public double getPinjaman() {
        return pinjaman;
    }

    public void setLamaPinjaman(int lamaPinjaman) {
        lamaPeminjaman = lamaPinjaman;
    }

    public int getLamaPeminjaman() {
        return lamaPeminjaman;
    }

    public void setDenda(double denda) {
        this.denda = denda;
    }

    public double getDenda() {
        return denda;
    }

    public void pinjam() {
        if (pinjaman > 0) {
            System.out.println("Silahkan anda lunasi terlebih dahulu pinjaman anda");
            System.out.println("==========================================="+"\n");
        } else {
            System.out.println("Selamat datang, "+nama+".");
            System.out.print("Silahkan masukkan nominal uang yang ingin dipinjam : ");
            double utang = inp.nextDouble();
            double saldo = getSaldoSistem();
            if (utang <= saldo) {
                setPinjaman(utang);
                setSaldoSistem(saldo-utang);
                System.out.print("Silahkan masukkan lama peminjaman : ");
                int tenggat = inp.nextInt();
                setLamaPinjaman(tenggat);
                System.out.println("Pinjaman anda telah berhasil");
                System.out.println("==========================================="+"\n");
            } else {
                System.out.println("Maaf nominal yang anda masukkan terlalu besar");
                System.out.println("==========================================="+"\n");
            }
        }
    }

    public void kembalikan() {
        double utang = getPinjaman();
        if (utang > 0) {
            System.out.println("Selamat datang, "+nama+".");
            System.out.print("Silahkan masukkan nominal uang yang ingin dikembalikan : ");
            double bayar = inp.nextDouble();
            System.out.print("Silahkan masukkan hari pengembalian : ");
            int dina = inp.nextInt();
            int dead = getLamaPeminjaman();
            if (dina > dead) {
                int f = dina - dead;
                double bunga = 15000*f;
                setDenda(bunga);
                setPinjaman(getPinjaman()+bunga);
                if (getPinjaman() - bayar < 0) {
                    System.out.println("Anda tidak boleh mengembalikan lebih dari pinjaman");
                    System.out.println("==========================================="+"\n");
                }
                else if(bayar <= getDenda()) {
                    System.out.println("Anda harus mengembalikan paling tidak lebih dari denda sebelumnya");
                    System.out.println("==========================================="+"\n");
                } else {
                    setPinjaman(getPinjaman()-bayar);
                    setSaldoSistem(getSaldoSistem()+bayar);
                }
                setLamaPinjaman(dina);
            } else {
                setPinjaman(getPinjaman()-bayar);
                setSaldoSistem(getSaldoSistem()+bayar);
            }
    
            if (getPinjaman() == 0) {
                System.out.println("Terima kasih telah melunasi pinjaman");
            } else {
                System.out.println("Terima kasih telah melunasi cicilan");
            }
            System.out.println("==========================================="+"\n");
        
            
        } else {
            System.out.println("Mohon maaf saudara/i "+nama+", Anda belum melakukan pinjaman");
            System.out.println("==========================================="+"\n");
        }
    }
}
