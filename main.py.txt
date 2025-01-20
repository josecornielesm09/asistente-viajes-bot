from telegram import Update
from telegram.ext import Updater, CommandHandler, MessageHandler, Filters, CallbackContext

# Reemplaza con tu token del bot de Telegram
TOKEN = "TU_TOKEN_AQUI"

def start(update: Update, context: CallbackContext) -> None:
    update.message.reply_text('¡Hola! Soy tu Asistente de Viajes. ¿En qué puedo ayudarte hoy?')

def handle_message(update: Update, context: CallbackContext) -> None:
    user_message = update.message.text
    respuesta_ia = "Aquí iría la respuesta procesada por la IA."
    update.message.reply_text(respuesta_ia)

def main():
    updater = Updater(TOKEN)
    dispatcher = updater.dispatcher

    # Comando /start
    dispatcher.add_handler(CommandHandler("start", start))
    # Responder mensajes
    dispatcher.add_handler(MessageHandler(Filters.text & ~Filters.command, handle_message))

    # Inicia el bot
    updater.start_polling()
    updater.idle()

if __name__ == "__main__":
    main()
