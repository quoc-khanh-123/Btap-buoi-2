using System;
using System.Collections.Generic;
using System.Linq;

class Student
{
    public int Id { get; set; }
    public string Name { get; set; }
    public int Age { get; set; }
}

class Program
{
    static void Main()
    {
        
        Console.OutputEncoding = System.Text.Encoding.UTF8;

        List<Student> students = new List<Student>()
        {
            new Student { Id = 1, Name = "Khánh", Age = 15 },
            new Student { Id = 2, Name = "Bình", Age = 16 },
            new Student { Id = 3, Name = "Cường", Age = 17 },
            new Student { Id = 4, Name = "Dũng", Age = 18 },
            new Student { Id = 5, Name = "Anh", Age = 15 }
        };

        
        Console.WriteLine("a. Danh sách toàn bộ học sinh:");
        foreach (var student in students)
        {
            Console.WriteLine($"Id: {student.Id}, Tên: {student.Name}, Tuổi: {student.Age}");
        }

       
        Console.WriteLine("\nb. Danh sách học sinh có tuổi từ 15 đến 18:");
        var age15to18 = students.Where(s => s.Age >= 15 && s.Age <= 18).ToList();
        foreach (var student in age15to18)
        {
            Console.WriteLine($"Id: {student.Id}, Tên: {student.Name}, Tuổi: {student.Age}");
        }

        
        Console.WriteLine("\nc. Học sinh có tên bắt đầu bằng chữ 'A':");
        var startsWithA = students.Where(s => s.Name.StartsWith("A")).ToList();
        foreach (var student in startsWithA)
        {
            Console.WriteLine($"Id: {student.Id}, Tên: {student.Name}, Tuổi: {student.Age}");
        }

        
        int totalAge = students.Sum(s => s.Age);
        Console.WriteLine($"\nd. Tổng tuổi của tất cả học sinh: {totalAge}");

        
        var oldestStudent = students.OrderByDescending(s => s.Age).FirstOrDefault();
        if (oldestStudent != null)
        {
            Console.WriteLine($"\ne. Học sinh có tuổi lớn nhất: Id: {oldestStudent.Id}, Tên: {oldestStudent.Name}, Tuổi: {oldestStudent.Age}");
        }

        
        Console.WriteLine("\nf. Danh sách học sinh sắp xếp theo tuổi tăng dần:");
        var sortedByAge = students.OrderBy(s => s.Age).ToList();
        foreach (var student in sortedByAge)
        {
            Console.WriteLine($"Id: {student.Id}, Tên: {student.Name}, Tuổi: {student.Age}");
        }
    }
}

