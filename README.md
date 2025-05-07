import telebot

bot = telebot.TeleBot("YOUR_TELEGRAM_BOT_TOKEN")

# Обработчик команды /start
@bot.message_handler(commands=['start'])
def send_welcome(message):
    bot.reply_to(message, "Привет! Я чат-бот Университета «Синергия». Задайте вопрос.")

# Обработка текстовых сообщений
@bot.message_handler(func=lambda message: True)
def reply_to_user(message):
    text = message.text.lower()
    
    if "привет" in text or "здравствуйте" in text:
        bot.reply_to(message, "Привет! Чем могу помочь?")
    elif "поступить" in text:
        bot.reply_to(message, "Для поступления подайте заявку на сайте synergy.ru.")
    elif "стоимость" in text:
        bot.reply_to(message, "Цены на обучение: [ссылка].")
    elif "контакты" in text:
        bot.reply_to(message, "Телефон: +7 (XXX) XXX-XX-XX, почта: info@synergy.ru.")
    elif "онлайн" in text:
        bot.reply_to(message, "Да, у нас есть дистанционное обучение. Подробнее: [ссылка].")
    else:
        bot.reply_to(message, "Извините, я не понял вопрос. Попробуйте уточнить.")

bot.polling()
