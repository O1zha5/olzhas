import datetime
import time
from IPython.display import Audio, display

def set_alarm(alarm_time, sound_file):
    """Устанавливает будильник на указанное время."""
    while True:
        current_time = datetime.datetime.now().strftime("%H:%M:%S")
        if current_time == alarm_time:
            print("Проснитесь! Время вставать!")
            display(Audio(sound_file, autoplay=True))
            break
        else:
            time.sleep(1)

def main():
    print("Добро пожаловать в будильник!")

    while True:
        alarm_time = input("Введите время для будильника в формате ЧЧ:ММ: ")
        try:
            datetime.datetime.strptime(alarm_time, "%H:%M")
            break
        except ValueError:
            print("Ошибка! Введите время в правильном формате.")

    sound_file = 'neon.mp3'  # Имя звукового файла (должен быть в том же каталоге, что и скрипт)

    print(f"Будильник установлен на {alarm_time}.")
    set_alarm(alarm_time, sound_file)

if __name__ == "__main__":
    main()
