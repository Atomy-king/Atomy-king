#include<iostream>
using namespace std;
#include<fstream>

class Person
{
public:
	char m_name[64];
	int m_age;
};

void test01()
{
	Person p1 = { "张三",18 };
	ofstream ofs;
	ofs.open("Person.txt", ios::out | ios::binary);
	ofs.write((const char*)&p1, sizeof(Person));
	ofs.close();
}

void test02()
{
	Person p2;
	ifstream ifs;
	ifs.open("Person.txt", ios::in | ios::binary);
	if (!ifs.is_open())
	{
		cout << "文件打开失败" << endl;
		return;
	}
	ifs.read((char*)&p2, sizeof(Person));
	cout << "姓名：" << p2.m_name << "  年龄：" << p2.m_age << endl;
	ifs.close();
}

int main()
{
	//test01();
	test02();
	return 0;
}
