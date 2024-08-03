# Algoritma-C#

## Soal 1

```using System;
namespace ReverseString
{
    class Program
    {
        static void Main(string[] args)
        {
            string input = "NEGIE1";
            string result = ReverseAlphabet(input);
            Console.WriteLine(result);
        }
        static string ReverseAlphabet(string input)
        {
            char[] chars = input.ToCharArray();
            int left = 0, right = chars.Length - 2; // Skip the last character (number)
            while (left < right)
            {
                if (char.IsLetter(chars[left]) && char.IsLetter(chars[right]))
                {
                    char temp = chars[left];
                    chars[left] = chars[right];
                    chars[right] = temp;
                    left++;
                    right--;
                }
                else
                {
                    if (!char.IsLetter(chars[left])) left++;
                    if (!char.IsLetter(chars[right])) right--;
                }
            }
            return new string(chars);
        }
    }
}
```
## Soal 2

```
using System;
using System.Linq;

namespace LongestWord
{
    class Program
    {
        static void Main(string[] args)
        {
            string sentence = "Saya sangat senang mengerjakan soal algoritma";
            var result = Longest(sentence);
            Console.WriteLine($"{result.word}: {result.length} character");
        }

        static (string word, int length) Longest(string sentence)
        {
            var words = sentence.Split(' ');
            var longestWord = words.OrderByDescending(w => w.Length).First();
            return (longestWord, longestWord.Length);
        }
    }
}
```
## Soal 3

```
using System;
using System.Collections.Generic;

namespace WordCount
{
    class Program
    {
        static void Main(string[] args)
        {
            string[] input = { "xc", "dz", "bbb", "dz", "dz", "ac", "ac", };
            string[] query = { "bbb", "ac", "dz" };
            int[] result = CountWords(input, query);
            Console.WriteLine(string.Join(", ", result));
        }

        static int[] CountWords(string[] input, string[] query)
        {
            Dictionary<string, int> wordCount = new Dictionary<string, int>();
            foreach (var word in input)
            {
                if (wordCount.ContainsKey(word))
                    wordCount[word]++;
                else
                    wordCount[word] = 1;
            }

            int[] result = new int[query.Length];
            for (int i = 0; i < query.Length; i++)
            {
                result[i] = wordCount.ContainsKey(query[i]) ? wordCount[query[i]] : 0;
            }
            return result;
        }
    }
}
```
## Soal 4
```
using System;

namespace MatrixDiagonal
{
    class Program
    {
        static void Main(string[] args)
        {
            int[,] matrix = {
                { 1, 2, 0 },
                { 4, 5, 6 },
                { 7, 8, 9 }
            };
            int result = DiagonalDifference(matrix);
            Console.WriteLine(result);
        }

        static int DiagonalDifference(int[,] matrix)
        {
            int n = matrix.GetLength(0);
            int primaryDiagonal = 0, secondaryDiagonal = 0;

            for (int i = 0; i < n; i++)
            {
                primaryDiagonal += matrix[i, i];
                secondaryDiagonal += matrix[i, n - i - 1];
            }

            return Math.Abs(primaryDiagonal - secondaryDiagonal);
        }
    }
}
```
