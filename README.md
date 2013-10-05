INFA-719
========

# Team 1
# Python code test set - not for use, just for github setup
## this list represents the round 1 seeding order on the tournament sheet
## this doesnt easily scale to 32, 64, 128 entries
teamlist = [1,16,8,9,5,12,4,13,6,11,3,14,7,10,2,15]  

#In a single elim tournament with a full field, # of games is # of teams-1
totalgames = len(teamlist) - 1

#Set defaults
gameid = 0
roundid = 0
nextround = []

#simulate all of the games
while gameid < totalgames:
    if gameid in [8,12,14]:  ##this is a manual decision tree, doesn't scale at all
        #if a new round begins, reset the list of the next round
        print "--- starting a new round of games ---"
        teamlist = nextround
        nextround = []
        roundid = 0

    #compare the 1st entry in the list to the 2nd entry in the list
    homeid = teamlist[roundid]
    awayid = teamlist[roundid + 1]

    #the winner of the match become the next entry in the nextround list
    #more realistic metrics could be substituted here, but ID can be used for this example
    if homeid < awayid:
        nextround.append(homeid)
        print str(homeid) + " vs " + str(awayid) + ":  The winner is " + str(homeid)
    else:
        nextround.append(awayid)
        print str(homeid) + " vs " + str(awayid) + ":  The winner is " + str(awayid)

    #increase the gameid and roundid
    gameid += 1
    roundid += 2
    print "next round matchup list: " + str(nextround)

print nextround
