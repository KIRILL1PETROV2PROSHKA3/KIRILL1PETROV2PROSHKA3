import discord
intents = discord.Intents.default()
intents.message_content = True

client = discord.Client(intents=intents)

@client.event
async def on_ready():
    print(f'We have logged in as {client.user}')

hello_words =['привет','hi','здравствуй','прив','ку']

@client.event
async def on_message(message):
    if message.author == client.user:
        return
    msg = message.content.lower()

    if msg in hello_words:
        await message.channel.send('и тебе привет, человек')
    elif message.content.startswith('$plastic'):
        await message.channel.send('Полимеры не выкидывают, а сдают на переработку. Прием ведут специализированные компании.')
    elif message.content.startswith('$glass'):
        await message.channel.send('Собирают битую тару, измельчают её в порошок, и уже его отправляют в дальнейшее производство; Целые стеклянные изделия чистят, дезинфицируют и используют повторно')
    else:
        await message.channel.send(message.content)

client.run('MTE2OTY2ODM4NDMwOTM5OTcwNg.G6S9pB.sJiCh1fzRCZonZCsIbTYCKFDOzQdgKicRHeO-8')
