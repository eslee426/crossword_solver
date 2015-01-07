Name: Elisha Lee
uni: esl2131
Assignment 3: Crossword Puzzle Solver


PART 1:
** you can update n in solve_puzzle
n = 0
Start Time:
11:23:06 PM
 runtime_before_fill : 0.37
 total_squares : 189.00
 matching_squares_before_fill : 175.00
 runtime_before_fill : 0.44
 total_squares : 187.00
 matching_squares_before_fill : 150.00
 runtime_before_fill : 0.30
 total_squares : 187.00
 matching_squares_before_fill : 118.00
 runtime_before_fill : 0.33
 total_squares : 188.00
 matching_squares_before_fill : 179.00
End Time:
11:23:10 PM

RUNTIME PER PUZZLE: 1 seconds


Start Time:
11:20:08 PM
n = 1
 runtime_before_fill : 6.67
 total_squares : 189.00
 matching_squares_before_fill : 175.00
 runtime_before_fill : 7.82
 total_squares : 187.00
 matching_squares_before_fill : 166.00
 runtime_before_fill : 5.29
 total_squares : 187.00
 matching_squares_before_fill : 139.00
 runtime_before_fill : 5.59
 total_squares : 188.00
 matching_squares_before_fill : 179.00
End Time:
11:20:38 PM

RUNTIME PER PUZZLE: 7.5 seconds

n = 2
Start Time:
11:09:31 PM
 runtime_before_fill : 104.62
 total_squares : 189.00
 matching_squares_before_fill : 175.00
 runtime_before_fill : 124.91
 total_squares : 187.00
 matching_squares_before_fill : 164.00
 runtime_before_fill : 80.31
 total_squares : 187.00
 matching_squares_before_fill : 137.00
 runtime_before_fill : 90.12
 total_squares : 188.00
 matching_squares_before_fill : 179.00
End Time:
11:16:16 PM

RUNTIME PER PUZZLE: ~ 2 minutes

n= 3
Start Time:
04:20:16 PM
 runtime_before_fill : 1509.72
 total_squares : 189.00
 matching_squares_before_fill : 175.00
 runtime_before_fill : 1718.02
 total_squares : 187.00
 matching_squares_before_fill : 174.00
 runtime_before_fill : 1123.79
 total_squares : 187.00
 matching_squares_before_fill : 150.00
 runtime_before_fill : 1393.08
 total_squares : 188.00
 matching_squares_before_fill : 179.00
End Time:
05:56:04 PM

RUNTIME PER PUZZLE: ~24 minutes

Performance:
I had pretty high accuracy for each of the monday puzzles. 
When n=0 --> I had an accuracy of 92.6%, 80.2%, 63.1%, 95.2% accuracy (respectively).
It took 1 second to solve each puzzle.
When n = 1 --> I had an accuracy of 92.6%, 88.8%, 74.33% and 95.2% accuracy (respectively)
Therefore, the lowest setting of n that lets my solver complete the puzzle with greater than 75%(with the exception of 3rd puzzle) -is n =1. This is before filling the blank squares. 
The highest setting of n that lets my solver complete each puzzle in less than 20 minutes is n =2. It ran each puzzle in approximately 2 minutes.
When n = 2 --> I had an accuracy of 92.6%, 87.7%, 73.3%, and 95.2% accuracy(respectively)
I obtained pretty high accuracy (with exception of 3rd puzzle), However for the middle 2 puzzles my accuracy dropped by a little amount. This may be due to some obscure edgecase
However, when n=3, accuracy improved for the middle 2 puzzles. It was able to solve each puzzle in approximately 24 minutes. 
When n = 3 --> I had an accuracy of 92.6%, 93.0%, 80.2% (FINALLY OVER 75%!), and 95.2% (respectively)
Surprisingly, the accuracy of the first and last puzzle have been consistent.

n determines how far the best solution can diverge from the greedy solution. In searching for the best solution, we pass in a greedy choice up to n times. If n=0, it is greedy.

Improve Performance:
I implemented the dr fill algorithm as given. I tried to not have as many nested loops. I improved performance simply by decreasing the runtime. I used default dictionaries, only deepcopied when necessary, and less checks.


PART 2:
After filling in blank squares, the solver's performance improved, but not by alot. It filled 3-5 squares on the Monday puzzles, and generally increased the number of correct by 1-2 entries. 

n=1
Start Time:
11:47:40 PM
 matching_squares_after_fill : 177.00
 total_squares : 189.00
 matching_squares_after_fill : 169.00
 total_squares : 187.00
 matching_squares_after_fill : 140.00
 total_squares : 187.00
 matching_squares_after_fill : 180.00
 total_squares : 188.00
End Time:
11:48:11 PM


n=2
Start Time:
11:38:47 PM
 matching_squares_after_fill : 177.00
 total_squares : 189.00
 matching_squares_after_fill : 169.00
 total_squares : 187.00
 matching_squares_after_fill : 138.00
 total_squares : 187.00
 matching_squares_after_fill : 180.00
 total_squares : 188.00
End Time:
11:45:33 PM



Algorithm:
-I obtained the solution from the solver, and inputted the solution into a fill_blanks method along with the puz object.
-In the method, I first initialize a words dictionary that will contain all the possible words. I get these words from the given answers_cwg_otsys.txt file.The key for the words is the length of the word, and the values are all the words that have that particular length. I use this method so I can look up word possibilities by word length.
-I then created a set of entries that need to be filled. I iterate through each entry of the solution, check if the entry word has a '-' character. If it does, I insert the entry into the set.
- I deepcopy the solution in order to return an updated version of the solution - i do this so I can access the previous solution
- I iterate through each entry in which the word needs to be filled. I obtain the word from the updated solution. I adjust the word so it would fit the regex format. For each possible word choice(by word lenght) - I regex search to see if a word can fit the entry. If a word exists, I add the word to the updated solution and I update the updated solution entirely to adjust for the new entry of the word.



PART 3:

ASSIGNED COMPONENT: 13. Brands
I adjusted this a little but, but finding a particular brand given the brand. 
HOW TO RUN: python brands_component.py < brand_clues.txt

CLUES: - Form test_month file
18A	Pepsi-owned beverage brand	4
6D	Insect repellent brand	3
19A	Body lotion brand	4
6D	Hasbro brand	4
52A	Shaving brand	4
50D	Skin-care brand	6
22A	Revlon brand	5
15D	Beverage brand portmanteau	6
39D	Food brand originally called Froffles	4


PERSONAL COMPONENT: SPORTS TEAMS
I adjusted this a little bit by filtering it to only relate to Major league NFL, NBA, NHL, and MLB teams in the united states. 
HOW TO RUN: python team_component.py < team_clues.txt

CLUES: - From clues.txt
1A	Phoenix NBA team	4
1D	WNBA team in Seattle	5
2A	Former (and likely future) Seattle NBA team	6
2D	Chicago's WNBA team	3
3A	St. Louis NFL team	4
3D	Detroit NFL team	5
4A	NHL team	5
4d	Phoenix's NHL team	7
5A	Tug McGraw's first MLB team	4
5D	NBA team	4

FOr both components, I use similar implementation. I create a dictionary to store word choices given a key word. For my assigned component, the key word was "brand" or brands. For my Personal Component, I had 2 key words = team and a particular Major league(NFL, NBA, NHL, MLB). Similar to the given state_capital component, I look through possible clues and word answers. For the assigned component, I obtained my dictionary data from the test_month. Inpiration for this method came from CWG. For my personal component, i obtained the dictionary information fron wikipedia. 
