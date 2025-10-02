import os
os.system("pip install telebot")
import random
import zlib
import base64
import marshal
import telebot
from telebot import types

# -------------------- Colors --------------------#
B = '\033[2;36m'
E = '\033[1;31m'
F = '\033[2;32m'
Z = '\033[1;91m'

print(f'''{F}━━━━━━━━━━━━━━━━━━⧪━━━━━━━━━━━━━━━━━━{B}
|{Z}[+] TeleGram  : {B} @wizardgotpain    |
|{Z}[+] Instagram : {B}@2v4xx            |
|{Z}[+] Tool      : {B} ENCRYPTION TOOL   |
|{Z}[+] Programmed By : {B} Wizard       |
{F}━━━━━━━━━━━━━━━━━━⧪━━━━━━━━━━━━━━━━━''')

# -------------------- Telegram Bot --------------------#
token = "8482093616:AAEKV3nLU_i7Gw5rKS5fYOc2DPjRbz7UyQQ"
bot = telebot.TeleBot(token)

# -------------------- Start Command --------------------#
@bot.message_handler(commands=['start'])
def start(message):
    buttons = [
        ("𝐌𝐀𝐑𝐒𝐇𝐀𝐋", 'marshal'),
        ("𝐁𝐀𝐒𝐄𝟔𝟒", 'base64'),
        ("𝐋𝐀𝐌𝐁𝐃𝐀", 'lambda'),
        ("𝐙𝐋𝐈𝐁", 'zlib2'),
        ("𝐌𝐀𝐑𝐒𝐇𝐀𝐋_𝐙𝐋𝐈𝐁", 'marshal_zlib'),
        ("𝐙𝐋𝐈𝐁_𝐁𝐀𝐒𝐄𝟏𝟔", 'zlib_base16'),
        ("𝐙𝐋𝐈𝐁_𝐁𝐀𝐒𝐄𝟑𝟐", 'base32_zlib'),
        ("𝐌𝐀𝐑𝐒𝐇𝐀𝐋_𝐙𝐋𝐈𝐁_𝐁𝐀𝐒𝐄𝟏𝟔", 'marshall_zlib_base16'),
        ("𝐌𝐀𝐑𝐒𝐇𝐀𝐋_𝐙𝐋𝐈𝐁_𝐁𝐀𝐒𝐄𝟔𝟒", 'marshall_zlib_base64'),
        ("🦅 EAGLE_SUPER", 'eagle_super'),
        ("🛡️ DAYS-HARD SUPER", 'days_hard')
    ]
    markup = types.InlineKeyboardMarkup(row_width=1)
    for text, data in buttons:
        markup.add(types.InlineKeyboardButton(text=text, callback_data=data))
    markup.add(types.InlineKeyboardButton(text="𝐏𝐑𝐎𝐆𝐑𝐀𝐌𝐌𝐄𝐃 𝐁𝐘", url="https://t.me/cyb3rx_eagle"))

    bot.send_message(message.chat.id,
                     "𝐖𝐄𝐋𝐂𝐎𝐌𝐄 𝐓𝐎 𝐖𝐈𝐙𝐀𝐑𝐃'𝐒 𝐄𝐍𝐂𝐑𝐘𝐏𝐓𝐈𝐎𝐍 𝐓𝐎𝐎𝐋. 𝐂𝐇𝐎𝐎𝐒𝐄 𝐓𝐇𝐄 𝐓𝐘𝐏𝐄 𝐎𝐅 𝐄𝐍𝐂𝐑𝐘𝐏𝐓𝐈𝐎𝐍.",
                     parse_mode="Markdown", reply_markup=markup)

# -------------------- Callback Handler --------------------#
@bot.callback_query_handler(func=lambda call: True)
def handle_callback(call):
    if call.data:
        bot.send_message(call.message.chat.id, f"Send the Python file for [{call.data}] encoding.")
        bot.register_next_step_handler_by_chat_id(call.message.chat.id, process_file, call.data)

# -------------------- Process Uploaded File --------------------#
def process_file(message, method):
    try:
        file_info = bot.get_file(message.document.file_id)
        downloaded = bot.download_file(file_info.file_path)
        rand_id = "".join(random.choice('0123456789') for _ in range(4))
        filename = f"{method}-{rand_id}.py"

        with open(filename, 'wb') as f:
            f.write(downloaded)

        encoded_code = encode_file(filename, method)

        with open(filename, 'w', encoding='utf-8') as f:
            f.write(encoded_code)

        with open(filename, 'rb') as doc:
            bot.send_document(message.chat.id, doc)

        os.remove(filename)
    except Exception as e:
        bot.send_message(message.chat.id, f"❌ Error: {e}")

# -------------------- Encoding Functions --------------------#
def encode_file(file_name, method):
    header = """#Encoded By 『ᴇᴀɢʟᴇ』
#Telegram - @cyb3rx_eagle
#Telegram Channel - @cyb3rx_portal

#_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-
# 🕵️‍♂️ Decoding this?
# 🔒 Its just a waste of time bro
# ⏳ Save your time for greatness.
#											  ~ᴇᴀɢʟᴇ"❤‍🩹
# ---------------------------------

"""
    code = open(file_name, 'r', encoding='utf-8').read()

    # -------------------- DAYS-HARD SAFE --------------------#
    if method == "days_hard":
        # First compression
        data = zlib.compress(code.encode())

        # Generate 3 random XOR layers
        keys = [random.randint(10, 255) for _ in range(3)]
        for k in keys:
            data = bytes([b ^ k for b in data])

        # Base85 encode and reverse
        data = base64.b85encode(data)[::-1]
        py_data = repr(data)

        # Add fake junk code outside compressed data
        fake_lines = "\n".join([
            f"# {random.randint(1000,9999)} useless line {i}" for i in range(5)
        ])

        return header + fake_lines + f"""
import zlib, base64
keys={keys}
data={py_data}
data=data[::-1]
data=base64.b85decode(data)
for k in reversed(keys):
    data=bytes([b ^ k for b in data])
exec(zlib.decompress(data).decode())
"""

    # -------------------- EAGLE_SUPER --------------------#
    elif method == "eagle_super":
        key = random.randint(10, 99)
        comp = zlib.compress(code.encode())
        xored = bytes([b ^ key for b in comp])
        encoded = base64.b85encode(xored)[::-1]
        return header + f"""import base64, zlib
key={key}
data={encoded}
data=data[::-1]
data=base64.b85decode(data)
data=bytes([b ^ key for b in data])
exec(zlib.decompress(data).decode())"""

    # -------------------- Marshal + zlib + base64 --------------------#
    elif method == "marshal_zlib_base64":
        s = base64.b64encode(zlib.compress(marshal.dumps(compile(code, 'module', 'exec'))))[::-1]
        return header + f"_ = lambda __ : __import__('marshal').loads(__import__('zlib').decompress(__import__('base64').b64decode(__[::-1])));exec((_)({s}))"

    # -------------------- Fallback --------------------#
    else:
        return code

# -------------------- Start Polling --------------------#
bot.polling(True)
