using System;
using System.Speech.Synthesis; // Необходимо установить пакет System.Speech через NuGet

namespace AccessibilityApp
{
    class Program
    {
        static void Main(string[] args)
        {
            SpeechSynthesizer synthesizer = new SpeechSynthesizer();
            synthesizer.SelectVoiceByHints(VoiceGender.Neutral);
            synthesizer.Speak("Добро пожаловать в приложение для людей с ограниченными возможностями!");

            int choice;
            do
            {
                synthesizer.Speak("Выберите опцию: 1 для управления уведомлениями, 2 для выхода.");
                Console.WriteLine("1. Управление уведомлениями");
                Console.WriteLine("0. Выход");
                Console.Write("Ваш выбор: ");
                choice = Convert.ToInt32(Console.ReadLine());

                switch (choice)
                {
                    case 1:
                        ManageNotifications(synthesizer);
                        break;
                    case 0:
                        synthesizer.Speak("Выход из программы.");
                        Console.WriteLine("Выход из программы.");
                        break;
                    default:
                        synthesizer.Speak("Неверный выбор. Попробуйте снова.");
                        Console.WriteLine("Неверный выбор. Попробуйте снова.");
                        break;
                }

            } while (choice != 0);
        }

        static void ManageNotifications(SpeechSynthesizer synthesizer)
        {
            int notificationChoice;
            do
            {
                synthesizer.Speak("Выберите опцию для управления уведомлениями: 1 для добавления, 2 для просмотра всех уведомлений, 0 для выхода.");
                Console.WriteLine("1. Добавить уведомление");
                Console.WriteLine("2. Просмотреть все уведомления");
                Console.WriteLine("0. Вернуться в главное меню");
                Console.Write("Ваш выбор: ");
                notificationChoice = Convert.ToInt32(Console.ReadLine());

                switch (notificationChoice)
                {
                    case 1:
                        AddNotification(synthesizer);
                        break;
                    case 2:
                        ViewNotifications(synthesizer);
                        break;
                    case 0:
                        synthesizer.Speak("Возврат в главное меню.");
                        Console.WriteLine("Возврат в главное меню.");
                        break;
                    default:
                        synthesizer.Speak("Неверный выбор. Попробуйте снова.");
                        Console.WriteLine("Неверный выбор. Попробуйте снова.");
                        break;
                }

            } while (notificationChoice != 0);
        }

        static void AddNotification(SpeechSynthesizer synthesizer)
        {
            Console.Write("Введите ваше уведомление: ");
            string notification = Console.ReadLine();
            // Здесь можно было бы сохранить уведомление в базе данных или файл
            synthesizer.Speak($"Уведомление добавлено: {notification}");
