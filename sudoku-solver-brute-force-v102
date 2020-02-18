import itertools

row1 = [7,5,1,8,4,6,9,2,3]
row2 = [6,8,3,7,9,2,4,5,1]
row3 = [9,2,4,1,5,3,6,7,8]
row4 = [2,3,8,6,7,1,5,4,9]
row5 = [1,7,5,9,3,4,2,8,6]
row6 = [4,0,6,5,2,8,0,3,0]
row7 = [5,6,2,0,1,7,8,0,0]
row8 = [8,0,7,2,0,9,0,1,5]
row9 = [0,1,0,4,8,5,0,6,2]
initialBoard = [ row1, row2, row3, row4, row5, row6, row7, row8, row9 ]
#potential improvements: start by checking if initialBoard is legal, e.g. [1,2,...,1] is not legal

#prune rowPossibles
legalDigits = [1,2,3,4,5,6,7,8,9]
rowPossibles = []
for rowGivens in initialBoard:
    rowPossibles.append([x for x in legalDigits if x not in rowGivens])

#generate permutationLists
permutations = []
for row in rowPossibles:
    print(row)
    permutations.append(list(itertools.permutations(row)))

#convert the inner tuples into lists
permutationsList = []
for permList in permutations:
    tempList = []
    for tupleSequence in permList:
        tempList.append(list(tupleSequence))
    permutationsList.append(tempList)

#loop through all combinations of permutationLists, 
#check solutionAttempt for correct answer
#break out of loop using function 'return' form
def solve(initialBoard,permutationsList) -> list:

    A = initialBoard.pop(0)
    B = initialBoard.pop(0)
    C = initialBoard.pop(0)
    D = initialBoard.pop(0)
    E = initialBoard.pop(0)
    F = initialBoard.pop(0)
    G = initialBoard.pop(0)
    H = initialBoard.pop(0)
    I = initialBoard.pop(0)

    seqsA = permutationsList.pop(0)
    seqsB = permutationsList.pop(0)
    seqsC = permutationsList.pop(0)
    seqsD = permutationsList.pop(0)
    seqsE = permutationsList.pop(0)
    seqsF = permutationsList.pop(0)
    seqsG = permutationsList.pop(0)
    seqsH = permutationsList.pop(0)
    seqsI = permutationsList.pop(0)

    for a in seqsA:
        #print("working hard")
        for b in seqsB:
            for c in seqsC:
                for d in seqsD:
                    #print("working harder")
                    for e in seqsE:
                        #print("working still")
                        for f in seqsF:
                            #print("working hardest")
                            for g in seqsG:
                                for h in seqsH:
                                    for i in seqsI:
                                        #print("working immediate")
                                        attempt = []
                                        attempt.append(applyRow(a,A))
                                        attempt.append(applyRow(b,B))
                                        attempt.append(applyRow(c,C))
                                        attempt.append(applyRow(d,D))
                                        attempt.append(applyRow(e,E))
                                        attempt.append(applyRow(f,F))
                                        attempt.append(applyRow(g,G))
                                        attempt.append(applyRow(h,H))
                                        attempt.append(applyRow(i,I))
                                        if (win_check(attempt) == True):
                                            return attempt #win
                            #break out of all loops using function return

#apply a permutation sequence to a row
#replace the 0 entries with the numbers from the sequence
def applyRow(sequence, boardRow) -> list:
    seq = sequence.copy()
    newRow = []
    for c in boardRow:
        if c == 0:
            newRow.append(seq.pop(0))
        else:
            newRow.append(c)
    return newRow

def win_check(solutionAttempt) -> bool:
    
    digits = list(range(1,10))
    
    #check rows
    for row in solutionAttempt:
        for n in digits:
        #if any digit occurs more than once, return false
            if (row.count(n) != 1):
                return False

    #check columns
    #generate column lists
    #repeat code sequence for testing single occurrence of "rows"
    tempBoard = []
    for i in range(len(solutionAttempt[0])):
        tempRow = []
        for row in solutionAttempt:
            tempRow.append(row[i])
          
        tempBoard.append(tempRow)
    
    #checking for duplicate digits
    for row in tempBoard:
        for n in digits:
            if (row.count(n) != 1):
                return False

    #check local 3x3 boxes
    #generate box lists
    #repeat code sequence for testing single occurrence
    
    #permutation of index combinations 0,1,2 / 3,4,5 / 6,7,8 
    #[0,1,2] and [0,1,2] top left box
    #[0,1,2] and [3,4,5] 
    #[0,1,2] and [6,7,8]

    #[4,5,6] and [0,1,2] mid left box
    #[4,5,6] and [3,4,5] 
    #[4,5,6] and [6,7,8]

    #[6,7,8] and [0,1,2] bot left box
    #[6,7,8] and [3,4,5] 
    #[6,7,8] and [6,7,8]

    tempBoard = []
    listCombs = [[0,1,2],[3,4,5],[6,7,8]]
    for b1 in listCombs:
        for b2 in listCombs:
            tempRow = []
            for r in b1:
                for c in b2:
                    tempRow.append(solutionAttempt[r][c])
            tempBoard.append(tempRow)

   #checking for duplicate digits
    for row in tempBoard:
        for n in digits:
            if (row.count(n) != 1):
                return False

    #all tests passed
    return True

print(solve(initialBoard,permutationsList))
