**Questions**
Lion Exhibition
As a lion trainer, you are taking part in an international lion exhibition. During the event lions from different teams enter and exit the showroom where lion experts can inspect and score them. 

Lions do not enter the showroom all at once, as that would cause too much commotion. The organizers of the event are letting them in and out based on a predefined schedule. Before the show starts you get access to the schedule for your lions - but not for the others. Nevertheless, during the show, you can observe all the lions getting in and out of the room.

Based on your experience, you believe that judges tend to award the biggest lions in the room with the highest scores. Before the final results are out, you want to estimate your chances of winning this competition.

Problem Statement
Complete the following functions:
The LionCompetion class constructor that  accepts lion descriptions and the private schedule of when the lions enter and exit the showroom. 
The Lionenterd and lionleft functions that are called whenever a new lion enters or leaves the room.
The getBiggestlions function that, for the current time, returns a list of our lions in the room that are at least as big as the biggest lion from competing teams in the room. The presented list has to be sorted alphabetically.

Function definitions 
LionCompetition class constructor parameters:
Lions, list elements describing your lions:
- name - string representing a name of the lion
- height - height of the lion

Schedule, a private schedule of when your lions enter and leave the show room 
- name - string representing a name of the lion
- enterTime - number of minutes since the start of the show when lion will enter the room
- exitTime - number of minutes since the start of the show when lion will exit the room

lionEntered function parameters:
currentTime - number of minutes since the start of show
height - height of the lion that entered the room 

lionLeft function parameters:
currentTime - number of minutes since the start of show
height - height of the lion that lefted the room 
 

Constraints
- Subsequent invocation of lionLeft and lionEntered functions are always called in order, according to the currentTime parameter. 
- the schedule is strictly followed - your lions enter and exit the room exactly at specidied times. 
- The lion inspection (invocation of the getBiggestLions function) takes place either before or after all lions scheduled to enter or leave the room at a given minute did that - never in between

- Lion names are unique 
- Times(currentTime, enterTime and exitTIme) are always whole numbers (and multiple events can occur at the same time)
- A single lion enters the room only once during the show.

The Sample Input for Custom Testing will be:
definition marry 300
definition rob 250
schedule marry 10 15
schedule rob 13 20
start 
8 enter 200 
10 enter 310 
10 enter 300
11 inspect 
13 enter 250
13 exit 310
13 inspect 
15 exit 300 
16 inspect
16 exit 200
20 exit 250
21 end

Sample output will be:
0
2 marry rob 
1 rob

Explanation
We have two lions:
Marry with a height of 300cm that enters the show 10 mintues after its start and exits it 15 mintues after its start
Rob with a height of 250cm that enters the show 13 mintues after its start and exits it 20 mintues after its start
The show goes as follows:
8 minutes after the start of the show a lion with a height of 200cm enters the room - based on the schedule it is not one of ours.
10 minutes after the start of the show two lions enter the room: a 310cm one and a 300cm one. The second one is Marry
We do an inspection, but unfortunately marry is not the biggest lion in the room, so we return an empty list.
13 mintues after the start of the show rob enters the room and the unknown 310cm lion exits it. 
We do an inspection. Both marry and rob are higher that the 200cm height lion that entered the room at the 8th mintue of the show, so we return both names.
15 minutes after start of the show marry leaves the room
we do an inspection. rob is still the biggest lion in the room.
16 and 20 mintues after the start of the show both remaining lions exit the room.
 

**Examples**

```
class LionCompetition:
    def __init__(self):
        self.lions = {}  # Definitions of our lions
        self.schedule = {}  # Schedule of our lions
        self.current_lions = set()  # Our lions currently in the room
        self.heights = []  # Heights of all lions in the room
        self.height_counts = {}  # Count of each height

    def definition(self, name, height):
        self.lions[name] = height

    def schedule_lion(self, name, enterTime, exitTime):
        self.schedule[name] = (enterTime, exitTime)

    def enter(self, currentTime, height):
        tmpName = "unknown"
        # Check if any of our lions entered at this time
        for name, (enterTime, exitTime) in self.schedule.items():
            if enterTime == currentTime and self.lions.get(name) == height:
                self.current_lions.add(name)
                tmpName = name
        # Add the height of the lion that entered
        self.heights.append((height, tmpName))


    def exit(self, currentTime, height):
        # Check if any of our lions left at this time
        tmpName = "unknown"
        for name, (enterTime, exitTime) in self.schedule.items():
            if exitTime == currentTime and self.lions.get(name) == height:
                self.current_lions.remove(name)
                tmpName = name
        # Remove the height of the lion that left
        self.heights.remove((height, tmpName))

    def inspect(self):
        # Find the maximum height among the lions in the room
        
        
        biggest_lions = []
        inspectHeights = sorted(self.heights.copy(), reverse=True)
        # print(inspectHeights)
        #print(self.current_lions)
        for h, name in inspectHeights:
            # print("name: %s"%name)
            if name in self.current_lions:
                biggest_lions.append(name)
            else:
                break
            
        # Filter our lions that are at least as big as this height
        # biggest_lions = [name for name in self.current_lions if self.lions[name] >= max_height]
        # Sort the result alphabetically and return
        # print(biggest_lions)
        return sorted(biggest_lions)

# Sample Test
competition = LionCompetition()
competition.definition("marry", 300)
competition.definition("rob", 250)
competition.schedule_lion("marry", 10, 15)
competition.schedule_lion("rob", 13, 20)
competition.enter(8, 200)
competition.enter(10, 310)
competition.enter(10, 300)
print(len(competition.inspect()))  # Expected: 0
competition.enter(13, 250)
competition.exit(13, 310)
print(len(competition.inspect()), " ".join(competition.inspect()))  # Expected: 2 marry rob
competition.exit(15, 300)
print(len(competition.inspect()), " ".join(competition.inspect()))  # Expected: 1 rob
competition.exit(16, 200)
competition.exit(20, 250)
```