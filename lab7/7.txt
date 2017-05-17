using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using static System.Console;

namespace lab7
{
    class Program
    {
        class Rational
        {
            int m, n;
            public Rational(int a, int b)
            {
                if (b == 0)
                {
                    m = 0; n = 1;
                }
                else
                {
                    m = a; n = b;
                }
            }
            public static Rational operator +(Rational r1, Rational r2)
            {
                return new Rational(r1.m * r2.n + r1.n * r2.m, r1.n * r2.n);
            }
            public static Rational operator -(Rational r1, Rational r2)
            {
                return new Rational(r1.m * r2.n - r1.n * r2.m, r1.n * r2.n);
            }
            public static Rational operator /(Rational r1, Rational r2)
            {
                return new Rational(r1.m * r2.n, r2.m * r1.n);
            }
            public static Rational operator *(Rational r1, Rational r2)
            {
                return new Rational(r1.m * r2.m, r1.n * r2.n);
            }
            public static bool operator >(Rational r1, Rational r2)
            {
                return (r1.m / r1.n > r2.m / r2.n);
            }
            public static bool operator <(Rational r1, Rational r2)
            {
                return (r1.m / r1.n < r2.m / r2.n);
            }
            public static bool operator ==(Rational r1, Rational r2)
            {
                return (r1.m / r1.n == r2.m / r2.n);
            }
            public static bool operator !=(Rational r1, Rational r2)
            {
                return (r1.m / r1.n != r2.m / r2.n);
            }
            public void print(string name)
            {
                WriteLine($"{name} = {m}/{n}");
            }
            private Rational(int a, int b, string t)
            {
                m = a; n = b;
            }
            public static readonly Rational Zero, One;
            static Rational()
            {
                Zero = new Rational(0, 1, "p");
                One = new Rational(1, 1, "p");
            }
        }
        class Person
        {
            string fam = "", status = "", health = "";
            int age = 0, salary = 0;
            public string Fam { get { return fam; } set { if(fam == "")fam = value; } }

            public string Status { get { return status; } }
            public int Age
            {
                set
                {
                    age = value;

                    if (age < 7) status = "children";

                    else if (age < 17) status = "schoolchild";

                    else if (age < 22) status = "student";

                    else status = "officer";

                }
                get { return age; }
            }
            public int Salary { set { salary = value; } }

            public Person()
            {
                age = salary = 0;
                status = health = fam = "";
            }
        }
        static void Main(string[] args)
        {
            Person p = new Person();
            p.Fam = "Sokolov";
            p.Fam = "new fam";
            p.Age = 19;
            p.Salary = 10000;
            WriteLine($"Surname = {p.Fam} => Status = {p.Status} => Age = {p.Age}");

            Rational r = new Rational(10, 6), r1 = new Rational(22, 16), r2 = new Rational(7, 1), r3;
            r.print("rational");
            r1.print("rational 1");
            r2.print("rational 2");
            r3 = r1 + r2;
            r3.print("Plus");
            r3 = r1 - r2;
            r3.print("Minus");
            r3 = r1 / r2;
            r3.print("Del");
            r3 = r1 * r2;
            r3.print("Multiplier");
            WriteLine($"r1 > r2 => {r1 > r2} | r < r2 => {r < r2} | r1 == r1 => {r1 == r1} | r1 != r2 => {Rational.Zero != r2}");
            ReadKey();
        }
    }
}