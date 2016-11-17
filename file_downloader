#!/usr/bin/env python
#coding: utf8

#Скачивает все прикреплённые файлы из треда

from termcolor import colored
import requests
import json
import urllib

domain = "https://2ch.pm"
url = input(colored("Thread URL: ", "magenta"))
print("")
url = url[:len(url)-4] + "json"
response = requests.get(url)
reply = response.json()
files = []

for element in reply["threads"][0]["posts"]:
	if element["files"] != []:
		print(colored("Thread-post:", "yellow"),colored(element["num"],"green"))
		for fl in element["files"]:
			print("> ", fl["displayname"], " -> ", fl["path"])
			displayname = fl["displayname"].replace("[...]","")
			files.append({"name": displayname, "path": fl["path"]})
			pass
		pass
	pass
reply = input(colored("Download (Y/n): ","magenta"))
print("")
if (reply == "y" or reply == "Y"):
	for element in files:
		load = urllib.request.urlopen(domain + element["path"]).read()
		f = open(element["name"], "wb")
		f.write(load)
		f.close()
		print(colored("Downloaded: ","green"), element["path"], " -> ", element["name"])
		pass
	pass
