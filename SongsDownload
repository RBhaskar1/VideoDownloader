#Script to download music from http://convert2mp3.net/en/index.php by copying the link from youtube

#import selenium to interact with web browser and objects in it
import selenium
from selenium import webdriver
from selenium.webdriver.common.keys import Keys
import time
from time import sleep

#to be used URLs
youtube = "https://www.youtube.com"
converter = "http://convert2mp3.net/en/index.php"
#Reading the songs to download from the file "songs-to-download" on the desktop
songList = open("/Users/rbhaskar/Desktop/songs-to-download","r")

#Just to test that we are able to read the list and dsiplay
#print songList.read()

for song in songList:
    #just stripping the white ends to make sure we remove unnecessary white spaces
    final_song = song.strip()

    #initiate the web browser
    chromedriver = '/Users/rbhaskar/Desktop/SongsDownloader/chromedriver'
    browser = webdriver.Chrome(chromedriver)
    browser.get(youtube)

    searchbar = browser.find_element_by_id("search")

    searchbar.send_keys(final_song)

    browser.find_element_by_id("search-form").submit()

    print "Sleeping"
    sleep(2)
    print "Woke up"

    videotitle = browser.find_element_by_id("video-title").get_attribute("title")

    if videotitle == final_song:

        hyperlink = browser.find_element_by_id("video-title").get_attribute("href")
        final_hyperlink = "https://www.youtube.com" + hyperlink

        browser2 = webdriver.Chrome(chromedriver)
        browser2.get(converter)

        convertURL = browser2.find_element_by_id("urlinput")
        convertURL.send_keys(final_hyperlink)
        browser2.find_element_by_class_name("mainbtn").submit()

        print "Sleeping"
        sleep(2)
        print "Woke up"

        browser2.find_element_by_class_name("btn-success").submit()

        print "Sleeping"
        sleep(2)
        print "Woke up"

        browser2.find_element_by_class_name("btn-success").click()

    else:
        print "Not in videotitle"
