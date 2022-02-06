# coding_club
import csv
import requests
response=requests.get('https://api.football-data.org/v2/competitions/')
football_info=response.json()
tiers=football_info['competitions']
tier_no=""
print("TIER_ONE")
print("TIER_SECOND")
print("TIER_THREE")
print("TIER_FOUR")
tier_value=input("enter the tier value:  \n")
if(tier_value=="1"):
    tier_no="TIER_ONE"
if(tier_value=="2"):
    tier_no="TIER_SECOND"
if(tier_value=="3"):
    tier_no="TIER_THREE"        
if(tier_value=="4"):
    tier_no="TIER_FOUR"    


with open("mycsv.csv","w",newline="") as f:
    thewriter=csv.writer(f)
    thewriter.writerow(['id','Name','Area/Country','Available_seasons','Tier_value'])
    for i in range(len(tiers)):
        if(tiers[i].get("plan")==tier_no):
            a=str(tiers[i].get("id"))
            b=tiers[i].get("name")
            c=tiers[i].get("plan")
            d=str(tiers[i].get("numberOfAvailableSeasons"))
            e=tiers[i].get("area").get("name")
            line=a+","+b+","+e+","+c+","+d
            array=line.split(',')
            thewriter.writerow(array)
