# NFL Big Data Bowl 2022
## by David Krejcarek

## Introduction

Before National Football League (NFL) coaches celebrate a big W, they strategize ways to improve field position and score points. Both of these objectives receive significant contributions from special teams plays, which consist of punts, kickoffs, field goals and extra points. These play types take on important roles in a game’s final score—so much so that coaches say they're a third of the game. Yet special teams remain an understudied part of American football, with an opportunity for data science to offer better ways to understand its impact.

The 2022 Big Data Bowl creates the opportunity for you (and the world!) to learn more about special teams play than ever before. We've provided the NFL's Next Gen Stats (NGS) tracking data from all 2018-2020 special teams plays. This data provides location information for each special teams player, wherever they are on the field, and includes their speed, acceleration, and direction. Additionally, and for the first time in Big Data Bowl history, participants can utilize scouting data from PFF, which supplements the tracking data with football specific metrics that coaches find critical to team success.

The NFL is America's most popular sports league. Founded in 1920, the organization behind American football has developed the model for the successful modern sports league. They're committed to advancing every aspect of the game, including the lesser researched special teams. In this competition, you’ll quantify what happens on special teams plays. You might create a new special teams metric, quantify team or individual strategies, rank players, or even something we haven’t considered.

With your creativity and analytical skills, the development of these new methods could lead to additional stats for special teams plays. If successful, your effort may even be adopted by the NFL for on air distribution, and you can watch future games knowing you had a hand in improving America's most popular sports league.

Summary of data
The 2022 Big Data Bowl data contains Next Gen Stats player tracking, play, game, player, and PFF scouting data for all 2018-2020 Special Teams plays. Here, you'll find a summary of each data set in the 2022 Data Bowl, a list of key variables to join on, and a description of each variable.

## Data 
    
### Summary of data

The 2022 Big Data Bowl data contains Next Gen Stats player tracking, play, game, player, and PFF scouting data for all 2018-2020 Special Teams plays. Here, you'll find a summary of each data set in the 2022 Data Bowl, a list of key variables to join on, and a description of each variable.

### File descriptions

Game data: The games.csv contains the teams playing in each game. The key variable is gameId.

Play data: The plays.csv file contains play-level information from each game. The key variables are gameId and playId.

Player data: The players.csv file contains player-level information from players that participated in any of the tracking data files. The key variable is nflId.

Tracking data: Files tracking[season].csv contain player tracking data from season [season]. The key variables are gameId, playId, and nflId.

PFF Scouting data: The PFFScoutingData.csv file contains play-level scouting information for each game. The key variables are gameId and playId.

Game data
> gameId: Game identifier, unique (numeric)
season: Season of game
week: Week of game
gameDate: Game Date (time, mm/dd/yyyy)
gameTimeEastern: Start time of game (time, HH:MM:SS, EST)
homeTeamAbbr: Home team three-letter code (text)
visitorTeamAbbr: Visiting team three-letter code (text)

Play data
>gameId: Game identifier, unique (numeric)
playId: Play identifier, not unique across games (numeric)
playDescription: Description of play (text)
quarter: Game quarter (numeric)
down: Down (numeric)
yardsToGo: Distance needed for a first down (numeric)
possessionTeam: Team punting, placekicking or kicking off the ball (text)
specialTeamsPlayType: Formation of play: Extra Point, Field Goal, Kickoff or Punt (text)
specialTeamsResult: Special Teams outcome of play dependent on play type: Blocked Kick Attempt, Blocked Punt, Downed, Fair Catch, Kick Attempt Good, Kick Attempt No Good, Kickoff Team Recovery, Muffed, Non-Special Teams Result, Out of Bounds, Return or Touchback (text)
kickerId: nflId of placekicker, punter or kickoff specialist on play (numeric)
returnerId: nflId(s) of returner(s) on play if there was a special teams return. Multiple returners on a play are separated by a ; (text)
kickBlockerId: nflId of blocker of kick on play if there was a blocked field goal or blocked punt (numeric)
yardlineSide: 3-letter team code corresponding to line-of-scrimmage (text)
yardlineNumber: Yard line at line-of-scrimmage (numeric)
gameClock: Time on clock of play (MM:SS)
penaltyCodes: NFL categorization of the penalties that occurred on the play. A standard penalty code followed by a d means the penalty was on the defense. Multiple penalties on a play are separated by a ; (text)
penaltyJerseyNumber: Jersey number and team code of the player committing each penalty. Multiple penalties on a play are separated by a ; (text)
penaltyYards: yards gained by possessionTeam by penalty (numeric)
preSnapHomeScore: Home score prior to the play (numeric)
preSnapVisitorScore: Visiting team score prior to the play (numeric)
passResult: Scrimmage outcome of the play if specialTeamsPlayResult is "Non-Special Teams Result" (C: Complete pass, I: Incomplete pass, S: Quarterback sack, IN: Intercepted pass, R: Scramble, ' ': Designed Rush, text)
kickLength: Kick length in air of kickoff, field goal or punt (numeric)
kickReturnYardage: Yards gained by return team if there was a return on a kickoff or punt (numeric)
playResult: Net yards gained by the kicking team, including penalty yardage (numeric)
absoluteYardlineNumber: Location of ball downfield in tracking data coordinates (numeric)

Player data
>nflId: Player identification number, unique across players (numeric)
Height: Player height (text)
Weight: Player weight (numeric)
birthDate: Date of birth (YYYY-MM-DD)
collegeName: Player college (text)
Position: Player position (text)
displayName: Player name (text)

PFF Scouting data
>gameId: Game identifier, unique (numeric)
playId: Play identifier, not unique across games (numeric)
snapDetail: On Punts, whether the snap was on target and if not, provides detail (H: High, L: Low, <: Left, >: Right, OK: Accurate Snap, text)
operationTime: Timing from snap to kick on punt plays in seconds: (numeric)
hangTime: Hangtime of player's punt or kickoff attempt in seconds. Timing is taken from impact with foot to impact with the ground or a player. (numeric)
kickType: Kickoff or Punt Type (text).
    Possible values for kickoff plays:
        D: Deep - your normal deep kick with decent hang time
        F: Flat - different than a Squib in that it will have some hang time and no roll but has a lower trajectory and hang time than a Deep kick off
        K: Free Kick - Kick after a safety
        O: Obvious Onside - score and situation dictates the need to regain possession. Also the hands team is on for the returning team
        P: Pooch kick - high for hangtime but not a lot of distance - usually targeting an upman
        Q: Squib - low-line drive kick that bounces or rolls considerably, with virtually no hang time
        S: Surprise Onside - accounting for score and situation an onsides kick that the returning team doesn’t expect. Hands teams probably aren't on the field
        B: Deep Direct OOB - Kickoff that is aimed deep (regular kickoff) that goes OOB directly (doesn't bounce)
    Possible values for punt plays:
        N: Normal - standard punt style
        R: Rugby style punt
        A: Nose down or Aussie-style punts
kickDirectionIntended: Intended kick direction from the kicking team's perspective - based on how coverage unit sets up and other factors (L: Left, R: Right, C: Center, text).
kickDirectionActual: Actual kick direction from the kicking team's perspective (L: Left, R: Right, C: Center, text).
returnDirectionIntended: The return direction the punt return or kick off return unit is set up for from the return team's perspective (L: Left, R: Right, C: Center, text).
returnDirectionActual: Actual return direction from the return team's perspective (L: Left, R: Right, C: Center, text).
missedTacklers: Jersey number and team code of player(s) charged with a missed tackle on the play. It will be reasonable to assume that he should have brought down the ball carrier and failed to do so. This situation does not have to entail contact, but it most frequently does. Missed tackles on a QB by a pass rusher are also included here. Multiple missed tacklers on a play are separated by a ; (text).
assistTacklers: Jersey number and team code of player(s) assisting on the tackle. Multiple assist tacklers on a play are separated by a ; (text).
tacklers: Jersey number and team code of player making the tackle (text).
kickoffReturnFormation: 3 digit code indicating the number of players in the Front Wall, Mid Wall and Back Wall (text).
gunners: Jersey number and team code of player(s) lined up as gunner on punt unit. Multiple gunners on a play are separated by a ; (text).
puntRushers: Jersey number and team code of player(s) on the punt return unit with "Punt Rush" role for actively trying to block the punt. Does not include players crossing the line of scrimmage to engage in punt coverage players in a "Hold Up" role. Multiple punt rushers on a play are separated by a ; (text).
specialTeamsSafeties: Jersey number and team code for player(s) with "Safety" roles on kickoff coverage and field goal/extra point block units - and those not actively advancing towards the line of scrimmage on the punt return unit. Multiple special teams safeties on a play are separated by a ; (text).
vises: Jersey number and team code for player(s) with a "Vise" role on the punt return unit. Multiple vises on a play are separated by a ; (text).
kickContactType: Detail on how a punt was fielded, or what happened when it wasn't fielded (text).
    Possible values:
        BB: Bounced Backwards
        BC: Bobbled Catch from Air
        BF: Bounced Forwards
        BOG: Bobbled on Ground
        CC: Clean Catch from Air
        CFFG: Clean Field From Ground
        DEZ: Direct to Endzone
        ICC: Incidental Coverage Team Contact
        KTB: Kick Team Knocked Back
        KTC: Kick Team Catch
        KTF: Kick Team Knocked Forward
        MBC: Muffed by Contact with Non-Designated Returner
        MBDR: Muffed by Designated Returner
        OOB: Directly Out Of Bounds

## Summary of Findings

> Summarize all of your findings from your exploration here, whether you plan on bringing them into your explanatory presentation or not.

We can see from the data that there are 4 types of Special team plays: Kickoff, Punt, Field Goal, Extra Point. We will be more interested on just the punt data in this review so we can reduce the infomation down to just play types that are Punt.  After reducing the data to just punting data we can take look at the what type of reuslts there are in a punt play.  I want to look at just a succesful punt.  Since we are intersted in successful punts, we need to look at what makes a punt returnable.  A returnable ball would allow the opposing team a chance to move the ball closer to scoring position.  A **fair Catch**  is when the returner signals he will catch bu twill not be able to move the ball forward towards the scoring positon. Lets keep the data simple and look at what type of punt results in a fair catch versus a returnable.  

The intial review of the the play type results of punts plats shows that the majority of the results appears to be a return followed by a fair catch. Taking a look at if these change over time, we see that Returns are still the most outcome followed by a fiar catch.  It is intersting to note that both Return and Fair Catches both go down.  This could be that punts in general went down between season.  It is also possible that if the number of punts remained the same but a other results increased. 

Plotting the kick length we can see that as a whole there a normal distribtion of the kick length with median being between 45 and 50 yards. Taking the review one step further and plotting the punt length over teh course of the seasons from 2018 to 2020, we see that there was consitancey over the course of the season.  THe meadian of all three season was just under 50 yards.  The distribution also seems similar when we look at this.  

Taking a look at the return yards we see that this is highly skewed to the right, with the majority of the returns falling between 0 and 5 yards.  Reviewing the Return yards over the course of the last three seasons there appears to be a consistancy through each season.  Although 2020 does display a slightly larger spread from 0 yard return to just under 10 yards the other season are with a yard or two of the spread.  

Another way to look at the return yards is to determine the average return yards per returner.  So I reworked the number to figure out the total return yards and the total number of returns by a player.  Divdiing these numbers we can get the average yards per return.  I first looked at the average yards per return as a whole and looking at that distribution of the yard per return avergae it appears that this is slightly skwed to the right with most returners averaging around 2.5 yards per return.  In 2018 there are two seperate peaks one at 0 yards and the at around 5 yards.  Which is interesting display considering that the other years it shows a more normal distribution.    These two peaks could be that when a player choose to return a ball in 2018 they had a much higher chance or were more successful in getting 5 yards every carry.  While the other two seasons it would appear that this is not the case.  The two peaks in the punting for 2018, might also be that the top two results was Return or a Fair Catch.  And these were more then other seasons.  The Fair catch would push the average down around zero and then a return it would appear that the average is 5 yards.  There is some room in this area to further dive into the this data and see of what factors of a kick contribute to a a fair catch versus a good retrun. It would appear that for years 2019 and 2020 the punt does not have a two distinct peaks but actually follows a more normal distribution.  But this isn't the same case as with  

Looking at the hang time is normally distrubuted with the median hang time is between 4.02 and 4.22 sec.  There does to be appear to have a slight skew to the left this seen by the long tail on the left but this is only a slight skew of the data.  This isn't that much of surprise of a distribution of punt Hang time.  



There doesn't seem to be any strong coorelation between the length of a punt as a whole.  The data plotted for all three season results in a over plot scatter and really takes away from being able to see any cluster patter. With the over plotting of data I reduced the data plots to season by season.  Even with a reduction of data there doesn't appear to be any significant correlation between the kick length and kick return.  It does look like that if there is a kick that is less than 35 yards there are few if any returns.  While any of punt that is less than 35 yards appears to be mostly ends in a fair catch.  But since there is no actual correlation between that and the return we will need to turn towards the hang time and see if there is a better correlation between that and the return length.  As we can see there really isn't any significant differeces between the season, moving forward it doens't make sense to split and instead look at this data as a whole.  

As seen earlier data points of this data set is pretty large, and results in overcrowding, a heatmap would make a better choice to see any patterns.  We can see that the majority of kicks had a hang time around the 4.5 sec, resulting in a kick length of 50 yards or so.  There isn't a clear correlation between hang time and kick length which I would think you see.  But since most of these kicks are clustered around a certain point it can really reduct the coorelation view.   We should take a look and see if there is a pattern with the hang time and kick length have an affect on the whether the punt will result in a fair catch or a return.  

From these three graphs we can see that Normal punt type has the highest Hang Time and also the longest kick.  The hang time for the Aussie stye is only slightly less then the hang time of Normal.  Although the graph doesn show a difference in the hang time we can see that the difference is with a 0.5 seconds of each other.  In reality that 1/2 second wouldn't really be noticed by anyone palying or watching.   However, we can see that the Aussie style with a kick length of about 40 yards doesn't get the same kick length as a normal kick wich as a median value of just under 50 yards.  The Rugby style is by far the worse form of kicking with the Hang time being almost 1/2 sec less then Normal Style and even worse the average is about 15 yards shorter. I would recommend staying away from that style.  

One important note is that the Aussie Style Type actaully results in more Fair Catches, while a normal kick results in significantly more Returns.  This is interesting because when we looked at the kick length and hang time they didn't really show a significant difference.  To really see what is going on we will need to see what affect the kick length and hang time together affect the play result.

We can see that there does seem to be a two clusters based on the hang time and kick length.  It is hard to really see what is happending so lets switch from a scatter plot to a heat map to see where the center of the two clusters are.  Lets change this to a heat map.

Splitting the data into the results of Return or Fair catch we can see that although the Hang time of the kicks for both Return and Fair Catches was about 4.5 sec the Fair catch could might be slightly.  The kick length shows a different story.  Although the hang time is similar we can see that the kick length changes, with a hang time of around 4.5 second and a about 50 yard to 55 yard, has a higher chance to be returned.  While a kick length of 40 to 45 yards has a higher chance of being downed as a fair catch.  If the goal would be to not have a return then the recommendation would be for punter to shoot for a high short kick.  This makes sense because this gives the gunners the best oppurtunity to get into position to force a Fair Catch call.  

One concern would be you are giving the opposing team about 10 yards by kicking it short.  Is this going to give the opposing team better field position.  As we showed earlier that the average return is usually between 2.5 and 7.5 yards and 78% of all returns are under 10 yards which would be less than or equal to having the punter kick the punt short.   At this point the recommendation would be for the punter to have a hang time og apprx 4.5 sec and get the ball within the 50 - 55 yard range.  This sets the team up with the highest chance of success.  Which would be defined as the opposing team have field position furthest from the endzone.  

## Key Insights for Presentation

> Select one or two main threads from your exploration to polish up for your presentation. Note any changes in design from your exploration step here.
