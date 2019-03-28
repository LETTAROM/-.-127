# -.-127
Наследование шаблонных классов. #127
#include <typeinfo>

class Point
{
public:
	Point()
	{
		x = y = z = 0;
	}
	Point(int x, int y, int z)
	{
		this->x = x;
		this->y = y;
		this->z = z;

	}
	double x; double y; double z;
};
template<typename  T1>//template значит что класс ниже шаблонный
class TypeSize
{
public:
	TypeSize(T1 value)//ктор принимает перем value т к зараннее неизвестно с каким типом данных б работать
	{
		this->value = value;
		
	}
	void DataTypeSize()//выводит инфу какое кол-во памяти в байтах занимает value T
	{
		cout << "value " << sizeof(value) << endl;//тип данных не указываем, т к тип
		
	}

protected://сделали протектид, чтообы перем б. видна всем потомкам но не пользователю
	//тогда мы сможем вывести ее в параметре метода typeid() и узнать типданных
	T1 value;//какого типа б. перем Т, мы укажем в <>в  MyClass<int> c(a);
	
};

template<typename T1>


class TypeInfo:public TypeSize<T1>//наследник класса TypeSize
{
	
public:
	TypeInfo(T1 value) :TypeSize(value)//вызываем констр базового класса и передаем в парам наштиип
	//данных value
	{

	}
	void ShowTypeName()//б. выводить инфу о типе данных с которым б. работать наш шаблон
	{
		cout << "Название типа " <<typeid(value).name() << endl;
		//typeid(value).name() метод выведит тип данных, переданный в value
	}
};
int main()
{
	int a = 2;
	TypeInfo<int> c(a);
	c.ShowTypeName();//название типа double
	c.DataTypeSize();//value 8



	return 0;
}


template<typename T>
class Stack
{
public:
	T result;
	Stack(T x,T y,T z)
	{
		this->x = x;
				this->y = y;
				this->z = z;
	}
	void Foo()
	{
		result = x+(y+z);
		cout <<x<<" "<<y<<" "<<z<<" + "<< result << endl;
	}
private:
	T x; T y; T z; 
};

int main()
{
	Stack<int> st(10, 2, 5);
	st.Foo();
	return 0;
}





#include<fstream>
#include<math.h>

template<typename T>

class Vvod
{
public:
	
	Vvod(T y)
	{
		this->y = y;
	}
	void foo()
	{			
		cout << "Введите числа, квадрат которых хотите получить!"<< endl;
		cin >> x;
      	cout <<"Квадрат введенных чисел: "<<pow(x, 2)<< endl;
    }	
private: T y;
		 T  x;
};
	


int main()
{

	setlocale(LC_ALL, "ru");
	
	Vvod <int> c(2);
	c.foo();
	
	string path = " ";
	cout << "Введите имя файла в формате txt" << endl;
	cin >> path;
	ofstream fout;
	fout.open(path,ofstream::app);
	if (!fout.is_open())
	{
		cout << "Ошибка токрытия файла!" << endl;
	}
	else
	{
		fout << "Файл успешно открыт!!" << endl;
	}
	
	
  
	fout.close();

	return 0;
}


