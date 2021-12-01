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


## Key Insights for Presentation

> Select one or two main threads from your exploration to polish up for your presentation. Note any changes in design from your exploration step here.