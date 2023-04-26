# szl_odlot_2
nienawdzie swojego zycoal wszy7uscu tylo narzekaja na menie i nie waracaja uwagu na mohe wmocje i to jak sie czuje maj de [presje i nie chce ab y to dlaje trwaoo n ie nedzioe ,mi soe zuc


using MySql.Data.MySqlClient;
using System;
using System.Collections.Generic;
using System.Globalization;
using System.Linq;
using System.Security.Cryptography.X509Certificates;
using System.Text;
using System.Threading.Tasks;
using Google.Protobuf.WellKnownTypes;
using MySql.Data.MySqlClient;
using System.Data.SqlClient;
using System.Xml.Linq;
using Mysqlx.Crud;
using Org.BouncyCastle.Utilities.Collections;

namespace projekt2137
{
    public class user
    {
        //public static bool czy_uzytkownik_zalogowany;
        //public static string login_uzytkownika_zalogowanego;
        public string login;
        public string password;
        public int level;
        //public static int poziom;


        public user(string login, string password, int level)
        {
            this.login = login;
            this.password = password;
            this.level = level;
        }
    }
    public class usery
    {
        public List<user> users = new List<user>();

        public void add_user(string new_login, string new_password)
        {
            if (string.IsNullOrEmpty(new_login) || string.IsNullOrEmpty(new_password))
            {
                Console.WriteLine("Nie można dodać pustego wiersza.");
                Console.ReadKey(true);
            }
            else
            {
                user user1 = new user(new_login, new_password, 1);
                users.Add(user1);
            }
        }
        static public bool CzyPoprawneLogowanie(string login, string password)
        {


                if (password == )
                {
    
                    return true;
                }
            }

            return false;
        }







        static public void Logowanie(string login, string password)
        {


            Console.Write("Witam, prosze podac login i haslo, aby uzyskać dostęp do rezerwowania lotów\n");
            Console.WriteLine("login:  ");
            login = Console.ReadLine();
            password = "";


            Console.WriteLine("haslo:  ");


            while (true)
            {
                ConsoleKeyInfo key = Console.ReadKey(true);

                if (key.Key == ConsoleKey.Enter)
                {

                    break;

                }

                // Jeśli użytkownik nacisnął klawisz Backspace, usuń ostatni znak z hasła
                if (key.Key == ConsoleKey.Backspace)
                {
                    if (password.Length > 0)
                    {
                        password = password.Substring(0, password.Length - 1);
                        Console.Write("\b \b"); // Usuń ostatni znak z ekranu
                    }
                }

                // Jeśli użytkownik nacisnął inny klawisz, dodaj go do hasła i wyświetl gwiazdkę
                if (key.KeyChar != '\u0000' && key.Key != ConsoleKey.Backspace)
                {
                    password += key.KeyChar;
                    Console.Write("*");
                }
                if (key.Key == ConsoleKey.Escape)
                {
                    Environment.Exit(0);
                    break;
                }
            }
            CzyPoprawneLogowanie(login, password);
            if (CzyPoprawneLogowanie(login, password) == true)
            {
                Console.WriteLine("\n\nZalogowano pomyslnie");
                czy_uzytkownik_zalogowany = true;
                login_uzytkownika_zalogowanego = login;
            }
            else
            {
                czy_uzytkownik_zalogowany = false;
                Console.WriteLine("\n\nBledne haslo lub login\nSproboj ponownie - enter\npowrot - escape");
                while (true)
                {
                    ConsoleKeyInfo key = Console.ReadKey(true);
                    if (key.Key == ConsoleKey.Enter)
                    {
                        Console.Clear();
                        Logowanie(conn);
                    }
                    else if (key.Key == ConsoleKey.Escape)
                    {
                        break;
                    }
                }

            }
        }

    }

}







































    //static public void add_user(MySqlConnection conn, string login, string password)
    //{
    //    if (string.IsNullOrEmpty(login) || string.IsNullOrEmpty(password))
    //    {
    //        Console.WriteLine("Nie można dodać pustego wiersza.");
    //        Console.ReadKey(true);
    //    }
    //    else
    //    {

    //        string insertQuery = "INSERT INTO user (login, password, level) VALUES (@login, @password, 1)";
    //        MySqlCommand command = new MySqlCommand(insertQuery, conn);
    //        command.Parameters.AddWithValue("@login", login);
    //        command.Parameters.AddWithValue("@password", password);

    //        conn.Open();
    //        int rowsAffected = command.ExecuteNonQuery();
    //        conn.Close();

    //        Console.WriteLine("{0} wiersz dodany do tabeli.", rowsAffected);
    //        Console.ReadKey(true);
    //    }

    //}



    //static public bool CzyPoprawneLogowanie(string login, string password, MySqlConnection conn)
    //{
    //    string selectQuery = "SELECT Password FROM user WHERE login = @login";
    //    MySqlCommand command = new MySqlCommand(selectQuery, conn);
    //    command.Parameters.AddWithValue("@login", login);

    //    conn.Open();
    //    MySqlDataReader reader = command.ExecuteReader();

    //    if (reader.HasRows)
    //    {
    //        reader.Read();
    //        string storedPassword = reader.GetString(0);

    //        if (password == storedPassword)
    //        {
    //            conn.Close();
    //            return true;
    //        }
    //    }

    //    conn.Close();
    //    return false;
    //}







    //static public void Logowanie(MySqlConnection conn)
    //{


    //    Console.Write("Witam, prosze podac login i haslo, aby uzyskać dostęp do rezerwowania lotów\n");
    //    Console.WriteLine("login:  ");
    //    string login = Console.ReadLine();
    //    string password = "";


    //    Console.WriteLine("haslo:  ");


    //    while (true)
    //    {
    //        ConsoleKeyInfo key = Console.ReadKey(true);

    //        if (key.Key == ConsoleKey.Enter)
    //        {

    //            break;

    //        }

    //        // Jeśli użytkownik nacisnął klawisz Backspace, usuń ostatni znak z hasła
    //        if (key.Key == ConsoleKey.Backspace)
    //        {
    //            if (password.Length > 0)
    //            {
    //                password = password.Substring(0, password.Length - 1);
    //                Console.Write("\b \b"); // Usuń ostatni znak z ekranu
    //            }
    //        }

    //        // Jeśli użytkownik nacisnął inny klawisz, dodaj go do hasła i wyświetl gwiazdkę
    //        if (key.KeyChar != '\u0000' && key.Key != ConsoleKey.Backspace)
    //        {
    //            password += key.KeyChar;
    //            Console.Write("*");
    //        }
    //        if (key.Key == ConsoleKey.Escape)
    //        {
    //            Environment.Exit(0);
    //            break;
    //        }
    //    }
    //    CzyPoprawneLogowanie(login, password, conn);
    //    if (CzyPoprawneLogowanie(login, password, conn) == true)
    //    {
    //        Console.WriteLine("\n\nZalogowano pomyslnie");
    //        czy_uzytkownik_zalogowany = true;
    //        login_uzytkownika_zalogowanego = login;
    //    }
    //    else
    //    {
    //        czy_uzytkownik_zalogowany = false;
    //        Console.WriteLine("\n\nBledne haslo lub login\nSproboj ponownie - enter\npowrot - escape");
    //        while (true)
    //        {
    //            ConsoleKeyInfo key = Console.ReadKey(true);
    //            if (key.Key == ConsoleKey.Enter)
    //            {
    //                Console.Clear();
    //                Logowanie(conn);
    //            }
    //            else if (key.Key == ConsoleKey.Escape)
    //            {
    //                break;
    //            }
    //        }

    //    }
    //}



    //static public void poziom_user(MySqlConnection conn, string login)
    //{
    //    string selectQuery = $"SELECT level FROM user WHERE login = {"@login"};";
    //    MySqlCommand command = new MySqlCommand(selectQuery, conn);
    //    command.Parameters.AddWithValue("@login", login);
    //    conn.Open();
    //    MySqlDataReader reader = command.ExecuteReader();
    //    reader.Read();
    //    int poziom = reader.GetInt32(0);
    //    level = poziom;

    //    reader.Close();
    //    conn.Close();
    //}












using MySql.Data.MySqlClient;
using System;
using System.Collections.Generic;
using System.Globalization;
using System.Linq;
using System.Security.Cryptography.X509Certificates;
using System.Text;
using System.Threading.Tasks;
using Google.Protobuf.WellKnownTypes;
using MySql.Data.MySqlClient;
using System.Data.SqlClient;
using System.Xml.Linq;
using Mysqlx.Crud;
using Org.BouncyCastle.Utilities.Collections;


namespace projekt2137
{
    internal class Program
    {
        static void Main(string[] args)
        {
            //string connectionString = "server=localhost;user id=root;password=;database=szl_odlot";
            //MySqlConnection conn = new MySqlConnection(connectionString);
            //user user = new user();
            ////Console.WriteLine("podaj login: ");
            ////string login = Console.ReadLine();
            ////Console.WriteLine("podaj haslo: ");
            ////string password = Console.ReadLine();
            //user.Logowanie(conn);
            Console.ReadKey(true);
        }
    }
}
