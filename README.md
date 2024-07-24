#include<iostream>
using namespace std;
#include<fstream>
#include<string>
struct NHANVIEN
{
	string ma;
	string ten;
	float songay;
	float luongngay;
	float thuclinh;
};
struct NODE
{
	NHANVIEN data;
	NODE* pNext;
};
typedef NODE* LIST;
NODE* create_node(NHANVIEN x)// data->node-list
{
	NODE* p = new NODE;
	if (p == NULL)
		return NULL;
	p->data = x;
	p->pNext = NULL;
	return p;
}
void create_list(LIST &l)
{
	l = NULL;
}
void add_head(LIST &l, NHANVIEN x)
{
	NODE* p = create_node(x);
	if (l == NULL)
		l = p;
	else
	{
		p->pNext = l;
		l = p;
	}
}
void add_tail(LIST &l, NHANVIEN x)
{
	NODE* p = create_node(x);
	if (l == NULL)
		l = p;
	else
	{
		NODE* Q = l;
		while (Q->pNext != NULL)
			Q = Q->pNext;
		Q->pNext = p;
	}
}
void nhap1nhanvien(NHANVIEN &NV)
{
	cin.ignore();
	cout << "Nhap ma: ";
	getline(cin, NV.ma);
	cout << "Nhap ten: ";
	getline(cin, NV.ten);
	cout << "Nhap ngay cong: ";
	cin >> NV.songay;
	cout << "Nhap luong ngay: ";
	cin >> NV.luongngay;
	NV.thuclinh = NV.luongngay*NV.songay;
}
void nhapDSNV(LIST &l, int n)
{
	NHANVIEN NV;
	for (int i = 1; i <= n; i++)
	{
		cout << "Nhop thong tin cho nhan vien thu " << i  << ": " << endl;
		nhap1nhanvien(NV);
		add_head(l, NV);
	}
}
void xuat1nhanvien(NHANVIEN NV)
{
	cout << NV.ma << "  " << NV.ten << "  " << NV.songay << "  " << NV.luongngay << "  " << NV.thuclinh << endl;
}
void xuatDSNV(LIST l)
{
	NODE *Q = l;
	while (Q != NULL)
	{
		xuat1nhanvien(Q->data);
		Q = Q->pNext;
	}
}
int main()
{
	LIST l;
	int n=2;
	create_list(l);
	nhapDSNV(l, n);
	cout << "\n DANH SACH VAI NHAP LA: \n";
	xuatDSNV(l);
	return 0;
}