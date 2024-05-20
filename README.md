# Create telbot

![TelBots](https://mli6mgta2eyj.i.optimole.com/w:1306/h:980/q:mauto/f:avif/https://propuskator.com/wp-content/uploads/2021/06/upravlenie-ustrojstvami-2smart-cloud-s-pomoshhyu-telegram-bota.png)

## Универсальный способ написания собственного телеграмм бота!

from aiogram import Bot, types
from aiogram.dispatcher import Dispatcher
from aiogram.utils import executor

from config import TOKEN

bot = Bot(token=TOKEN)
dp = Dispatcher(bot)


@dp.message_handler(commands=['start'])
async def process_start_command(message: types.Message):
    await message.reply("Привет!\nНапиши мне что-нибудь!")


@dp.message_handler(commands=['help'])
async def process_help_command(message: types.Message):
    await message.reply("Напиши мне что-нибудь, и я отпрпавлю этот текст тебе в ответ!")


@dp.message_handler()
async def echo_message(msg: types.Message):
    await bot.send_message(msg.from_user.id, msg.text)


if __name__ == '__main__':
    executor.start_polling(dp)

### Стандартный синтаксис *Python* кода для написания *ЭХО БОТА*