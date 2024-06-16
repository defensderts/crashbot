import discord
from discord.ext import commands
from asyncio import sleep
from discord.utils import get

import discord
from discord.ext import commands

TOKEN = 'token'
intents = discord.Intents.all()
bot = commands.Bot(command_prefix=".", intents=intents)

@bot.command(pass_context=True)
async def spam(ctx, m):
    await ctx.message.delete() 
    count = 0
    while count < int(m):
        await ctx.send("сообщения") 
        count += 1

@bot.command(pass_context=True)
async def spam_channel(ctx, m):
    await ctx.message.delete()
    count1 = 0
    while count1 < int(m):
        guild = ctx.message.guild
        await guild.create_text_channel('название канала ')
        count1 += 1



@bot.command()
async def add_role(ctx, member: discord.Member, role: discord.Role):
    try:
        await member.add_roles(role)
        await ctx.send(f"Роль {role.name} была выдана {member.mention}")
    except discord.Forbidden:
        await ctx.send("У меня недостаточно прав для выполнения этой операции.")
    except discord.HTTPException:
        await ctx.send("Не удалось выполнить операцию из-за ошибки на стороне Discord.")


@bot.command()
async def remove_role(ctx, member: discord.Member, role: discord.Role):
    try:
        await member.remove_roles(role)
        await ctx.send(f"Роль {role.name} была снята с {member.mention}")
    except discord.Forbidden:
        await ctx.send("У меня недостаточно прав для выполнения этой операции.")
    except discord.HTTPException:
        await ctx.send("Не удалось выполнить операцию из-за ошибки на стороне Discord.")


@bot.event
async def on_ready():
    print(f'Бот {bot.user} подключен к Discord!')

@bot.command()
async def delete_all_channels(ctx):
    
    if ctx.author.guild_permissions.administrator:
        
        for channel in ctx.guild.channels:
            await channel.delete()
        await ctx.send("Все каналы на сервере были удалены.")
    else:
        await ctx.send("У вас недостаточно прав для выполнения этой операции.")

bot.run(TOKEN)
