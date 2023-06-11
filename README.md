# epayTest1

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp1
{

    internal class Program
    {
        static void Main(string[] args)
        {
            string userInput;
            int intVal;

            Console.Write("Enter amount: ");
            userInput = Console.ReadLine();
            intVal = Convert.ToInt32(userInput);
            var cco = new Dictionary<string, int>();

            var coc = new Dictionary<int, int[]>()
            {
                {1, new[]{ 10, 50, 100 }},
                {2, new[]{ 10, 100, 50 }},
                {3, new[]{ 50, 10, 100 }},
                {4, new[]{ 50, 100, 10 }},
                {5, new[]{ 100, 50, 10 }},
                {6, new[]{ 100, 10, 50 }}
            };

            foreach (var c in coc)
            {

                var inputAmount = intVal;
                var intervals = c.Value;


                if (inputAmount % 10 != 0)
                {
                    Console.Write("Only bills of in increments of 10 are dispensed");
                    return;
                }

                foreach (var interval in intervals)
                {
                    int count = inputAmount / interval;
                    inputAmount = inputAmount % interval;

                    if (count != 0)
                    {
                        int k = 0;

                        if (c.Key == 2 || c.Key == 4 || c.Key == 6)
                            k = 1;
                        else
                            k = 0;

                        if (!cco.ContainsKey(count.ToString() + "-" + interval.ToString() + "-" + ((c.Key) - k).ToString()))
                        {
                            Console.WriteLine("{0}*{1} EURO", count, interval);
                            cco.Add(count.ToString() + "-" + interval.ToString() + "-" + ((c.Key) - k).ToString(), interval);
                        }

                    }

                }

                Console.WriteLine("   ");

            }

            Console.Read();
        }

    }
}
