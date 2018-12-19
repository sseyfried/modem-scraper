#! /usr/bin/python

# modem-scraper
# scrapes data from an SB141

import bs4 as bs
import urllib
import datetime
#import pandas as pd

now = datetime.datetime.now()

#source = urllib.urlopen('http://192.168.100.1/cmSignal.htm').read() #sb6141
source = urllib.urlopen('http://192.168.100.1/cmSignalData.htm').read() #sb6141_datapage
#source = urllib.urlopen('http://192.168.100.1/RgConnect.asp').read() #zoom

soup = bs.BeautifulSoup(source,'lxml')

#print(soup.table.get_text())
#print(soup.get_text())

#allText = soup.get_text()
#f = open('sb141_logs.csv','a')
#print >> f, allText.encode("utf-8")

#table = soup.find_all('table')

table_rows = soup.find_all('tr')

for tr in table_rows:
	td = tr.find_all('td')
	row = [i.text for i in td]
	print str(now)	
	print (row)
	#f = open('sb141_logs.csv','a')
	#print >> str(now)
	#print >> f, row

#dfs = pd.read_html('http://192.168.100.1/cmSignalData.htm',header=0)
#for df in dfs:
	#print(df)
