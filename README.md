import java.util.Scanner;
 
class TaiLieu {
    String maTaiLieu, tenNhaXuatBan;
    int soBanPhatHanh;
    Scanner scan = new Scanner(System.in);
 
    public void input( ) {
        System.out.print("Nhap ma tai lieu: ");
        maTaiLieu = scan.nextLine();
        System.out.print("Nhap ten nha xuat ban: ");
        tenNhaXuatBan = scan.nextLine();
        System.out.print("Nhap so ban phat hanh: ");
        soBanPhatHanh = scan.nextInt();
        //scan.nextLine();
        //scan.close();
    }
 
    public void output( ) {
        System.out.printf("%20s %20s %20s %20s %20s %20s %20s %20sn",
                "Ma Tai Lieu", "Nha Xuat Ban", "So Ban Phat Hanh",
                "Tac Gia Sach", "So Trang Sach", "So Phat Hanh",
                "Thang Phat Hanh", "Ngay Phat Hanh");
        System.out.printf("%20s %20s %20d", maTaiLieu,
                tenNhaXuatBan, soBanPhatHanh);
    }
    public void close() {
            scan.close();
    }
}
 
class Sach extends TaiLieu implements Type {
    String tenTacGia;
    int soTrang;
 
    @Override
    public void input( ) {
        super.input( );
        System.out.print("Nhap ten tac gia cuon sach: ");
        tenTacGia = scan.nextLine();
        System.out.print("Nhap so trang cuon sach: ");
        soTrang = scan.nextInt();
        //scan.nextLine();
        //scan.close();
    }
 
    public void output( ) {
        super.output();
        System.out.printf("%20s %20d %20s %20s %20s", tenTacGia,
                soTrang, " ", " ", " ");
    }
}
 
class TapChi extends TaiLieu implements Type {
    String soPhatHanh;
    int thangPhatHanh;
 
    @Override
    public void input( ) {
 
    }
 
    public void output( ) {
        System.out.printf("%20s %20s %20s %20d %20s", " ", " ",
                soPhatHanh, thangPhatHanh, " ");
    }
}
 
class Bao extends TaiLieu implements Type {
    int ngayPhatHanh;
 
    @Override
    public void input( ) {
 
    }
 
    public void output( ) {
        System.out.printf("%20s %20s %20s %20d %20s", " ", " ", " ",
                ngayPhatHanh, " ");
    }
}
 
interface Type {
    public void input( );
 
    public void output( );
}
 
public class QuanLyThuVien {
    int n;
    TaiLieu taiLieu[];
 
    public void input() {
        Scanner scan = new Scanner(System.in);
        System.out.print("Nhap so tai lieu: ");
        n = scan.nextInt();
        scan.nextLine();
        taiLieu = new TaiLieu[n];
 
        for (int i = 0; i < n; i++) {
            System.out.print("Nhap loai tai lieu: (sach, tapchi, bao) ");
            String loai = scan.nextLine();
            if (loai.equals("sach")) taiLieu[i] = new Sach();
            else if (loai.equals("tapchi")) taiLieu[i] = new TapChi();
            else if (loai.equals("bao")) taiLieu[i] = new Bao();
            else continue;
            taiLieu[i].input();
        }
        scan.close();
    }
 
    public void output() {
        for (int i = 0; i < n; i++) {
            taiLieu[i].output();
        }
    }
 
    public static void main(String[] args) {
        QuanLyThuVien ql = new QuanLyThuVien();
        ql.input();
        ql.output();
    }
} 
