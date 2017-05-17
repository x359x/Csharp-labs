using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using static System.Console;

namespace lab8
{
    class Program
    {
        static void Main(string[] args)
        {
            Trainn t = new Trainn("1A2V", "Start", 6, typeTraine.skTrain);
            WriteLine($"{t.ToString()}");

            SByte a = 0;
            Byte b = 0;
            Int16 c = 0;
            Int32 d = 0;
            Int64 e = 0;
            String s = "";
            Exception ex = new Exception();
            Object[] types = {a,b,c,d,e,s,ex, new Trainn(), new Program(), new int[] { 1, 2, 3 } };

            foreach (var item in types)
            {
                WriteLine($"{item.GetType().Name}-{item.GetType().IsValueType}");
            }

            FirmTrain ft = new FirmTrain("Фирменное название", 1.6 ,"1A2V", "Start", 6, typeTraine.skTrain);
            WriteLine($"{ft}");

            list<int> l = new list<int>();
            kl.Add(1);
            l.Add(2);
            l.Add(3);

            l.Print();

            ReadKey();
        }
    }
}

enum typeTraine
{
    skTrain = 0,
    pasTrain = 1,
    tTrain = 2,
    None = -1
}
class list<T>
{
    class listItem<T>
    {

        public listItem<T> Next { get; set; }
        public T Value { get; set; }

        public listItem(listItem<T> next, T value)
        {
            Next = next;
            Value = value;
        }
    }

    private listItem<T> _head = null;
    private listItem<T> _tail = null;

    public list() { }
    public void Add(T value)
    {
        listItem<T> temp = new listItem<T>(null, value);
        if (_head == null)
        {
            _head = _tail = temp;
            _head.Next = _tail;
        }
        else
        {
            _tail.Next = temp;
            _tail = temp;
        }
    }

    public void Print()
    {
        listItem<T> temp = _head;
        while (temp != null)
        {
            WriteLine(temp.Value);
            temp = temp.Next;
        }
    }
}
class FirmTrain: Train
{
    public string nameFirm;
    private double kPrice;

    public FirmTrain(string name, double k, string num, string mes, int n, typeTraine t) : base(num, mes, n , t)
    {
        nameFirm = name;
        kPrice = k;
    }

    public override string ToString()
    {
        return nameFirm + "-" + kPrice + "-" + base.ToString();
    }
}
class Train
{
    public int count;
    public string number;
    public string message;
    public int typeTrain;

    public Train(string num = "", string mes = "", int n = 0, typeTraine t = typeTraine.None)
    {
        count = n;
        message = mes;
        number = num;
        typeTrain = (int)t;
    }
    public override string ToString()
    {
        string str;
        str = typeTrain == 0 ? "скорый поезд" : typeTrain == 1 ? "пассажирский поезд" : typeTrain == 2 ? "товарный поезд" : "None";
        return str + "-" + number + "-" + message + "-" + count;
    }
}
struct Trainn
{
    public int count;
    public string number;
    public string message;
    public int typeTrain;

    public Trainn(string num = "", string mes = "", int n = 0, typeTraine t = typeTraine.None)
    {
        count = n;
        message = mes;
        number = num;
        typeTrain = (int)t;
    }
    public override string ToString()
    {
        string str;
        str = typeTrain == 0 ? "скорый поезд" : typeTrain == 1 ? "пассажирский поезд": typeTrain  == 2 ?"товарный поезд" : "None";
        return str + "-" + number + "-" + message + "-" + count;
    }
}
