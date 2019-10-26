
import turtle
import time
import random
import copy



the_board = [ "1", "2", "3",
              "4", "5", "6",
              "7", "8", "9"]
#tracks how many moves the user placed
count=0
turtle.pensize(5)
def draw_board(board):
    turtle.clear()
    #prints the grid
    #turtle.setup(350,350)
    for i in range(-150,250, 100):
        turtle.up()
        turtle.goto(150,-i)
        turtle.down()
        turtle.goto(-150,-i)
    for i in range(-150,250, 100):
        turtle.up()
        turtle.goto(-i,150)
        turtle.down()
        turtle.goto(-i,-150)
    track=0
    #prints player's move
    for b in range(0,len(board)):
        if board[b]=="o":
            c=b
            if b<3:
                track=0
            elif b<6:
                track=1
                c-=3
            elif b<9:
                track=2
                c-=6
              #  print(c, track)
            c+=1
            track+=1
            move((c*100-200),-(track*100-180))
            turtle.circle(20)
    #prints computer move
    for b in range(0,len(board)):
        if board[b]=="x":
            c=b
            if b<3:
                track=0
            elif b<6:
                track=1
                c-=3
            elif b<9:
                track=2
                c-=6
            #    print(c, track)
            c+=1
            track+=1
            move((c*100-200),-(track*100-200))
            turtle.color("red")
            #draws Cross
            turtle.right(45)
            turtle.forward(20)
            turtle.right(180)
            turtle.forward(40)
            turtle.right(180)
            turtle.forward(20)
            turtle.right(90)
            turtle.forward(20)
            turtle.right(180)
            turtle.forward(40)
            turtle.right(180)
            turtle.forward(20)
            turtle.setheading(0)
            turtle.color("black")

    turtle.update()
    
def move(x,y):
    turtle.up()
    turtle.goto(x,y)
    turtle.down()
    
def do_user_move(board, x, y):
 #   print("user clicked at "+str(x)+","+str(y))
 #checks which grid the user clicked in and makes sure its available
    if -150<x<-50: 
        if 50<y<150 and board[0]!="o" and board[0]!="x":
            board[0]="o"
            return True
        elif -50<y<50 and board[3]!="o" and board[3]!="x":
            board[3]="o"
            return True
        elif -150<y<-50 and board[6]!="o" and board[6]!="x":
            board[6]="o"
            return True
    elif -50<x<50: 
        if 50<y<150 and board[1]!="o" and board[1]!="x":
            board[1]="o"
            return True
        elif -50<y<50 and board[4]!="o" and board[4]!="x":
            board[4]="o"
            return True
        elif -150<y<-50 and board[7]!="o" and board[7]!="x":
            board[7]="o"
            return True
    elif 50<x<150:
        if 50<y<150 and board[2]!="o" and board[2]!="x":
            board[2]="o"
            return True
        elif -50<y<50 and board[5]!="o" and board[5]!="x":
            board[5]="o"
            return True
        elif -150<y<-50 and board[8]!="o" and board[8]!="x":
            board[8]="o"
            return True
    else:
        return False
    

def check_game_over(board):
    global count
    #if there are three of a kind in a row, it ends the game
    #checks if result is "o" winning
    if (board[0]==board[1]==board[2] and board[1]=="o") or\
        (board[2]==board[5]==board[8] and board[2]=="o") or\
        (board[0]==board[3]==board[6] and board[0]=="o") or\
        (board[6]==board[7]==board[8] and board[8]=="o") or\
        (board[1]==board[4]==board[7] and board[1]=="o") or\
        (board[3]==board[4]==board[5] and board[3]=="o") or\
        (board[0]==board[4]==board[8] and board[0]=="o") or\
        (board[2]==board[4]==board[6] and board[2]=="o"):
        #resets board
        for i in range(1,10):
            board[i-1]=i
        count=0
        #displays statement on screen
        turtle.goto(0,0)
        time.sleep(1)
        turtle.clear()
        turtle.write("Well done", move=False, align="center", font=("Arial", 20, "normal"))
        time.sleep(1)
        draw_board(board)
        return True
    #checks if result is "x" winning
    elif (board[0]==board[1]==board[2] and board[1]=="x") or\
        (board[2]==board[5]==board[8] and board[2]=="x") or\
        (board[0]==board[3]==board[6] and board[0]=="x") or\
        (board[6]==board[7]==board[8] and board[8]=="x") or\
        (board[1]==board[4]==board[7] and board[1]=="x") or\
        (board[3]==board[4]==board[5] and board[3]=="x") or\
        (board[0]==board[4]==board[8] and board[0]=="x") or\
        (board[2]==board[4]==board[6] and board[2]=="x"):
        #prints statement on screen
        time.sleep(1)
        turtle.goto(0,0)
        turtle.clear()
        turtle.write("Try Again", move=False, align="center", font=("Arial", 20, "normal"))
        time.sleep(1)
        draw_board(board)
        #resets board
        for i in range(1,10):
            board[i-1]=i
        count=0
        draw_board(board)
        return True
    else:
        #if player went five moves and no one wins
        #ties
        if count==5:
            #resets baord
            for i in range(1,10):
                board[i-1]=i

            #prints statement on screen
            count=0
            time.sleep(1)
            turtle.clear()
            turtle.goto(0,0)
            turtle.write("Tie", move=False, align="center", font=("Arial", 20, "normal"))
            time.sleep(1)
            draw_board(board)
            return True
        return False

def two_in_tuple(board,d,e,f,turn):
    a=board[d]
    b=board[e]
    c=board[f]
   
    if a==b==c:
        return -1,False
    elif a==b and a!=c and c!="x" and c!="o":
        return f,a==turn
    elif a==c and a!=b and b!="x" and b!="o":
        return e,c==turn
    elif b==c and b!=a and a!="x" and a!="o":
        return d,b==turn
    else:
        return -1,False
        
def do_computer_move(board):

    if count==0 and board[4]=="o":
        number=random.choice([0,2,6,8])
        board[number]="x"
        return

    #iterates through the horizontal rows searching for two "x" in a row
    for i in range(0,7,3):
        holder=two_in_tuple(board,i,i+1,i+2, "x")
        if holder[0] != -1 and holder[1]:
            board[holder[0]]="x"
            return
            
    #iterates through the vertical rows searching for two "x" in a row        
    for s in range(3):
        holder=two_in_tuple(board,s,s+3,s+6,"x")
        if holder[0] != -1 and holder[1]:
            board[holder[0]]="x"
            return
    #iterates through the horizontal rows searching for two "o" in a row   
    for i in range(0,7,3):
        holder=two_in_tuple(board,i,i+1,i+2,"o")
        if holder[0] != -1 and holder[1]:
            board[holder[0]]="x"
            return
    #iterates through the vertical rows searching for two "o" in a row                    
    for s in range(3):
        holder=two_in_tuple(board,s,s+3,s+6,"o")
        if holder[0] != -1 and holder[1]:
            board[holder[0]]="x"
            return
#Check if diagnal "o" win
    holder=two_in_tuple(board,0,4,8,"o")
    if holder[0] != -1 and holder[1]:
        board[holder[0]]="x"
        return

    holder=two_in_tuple(board,2,4,6,"o")
    if holder[0] != -1 and holder[1]:
            board[holder[0]]="x"
            return
        
#Check if diagnal "x" win
    holder=two_in_tuple(board,0,4,8,"x")
    if holder[0] != -1 and holder[1]:
        board[holder[0]]="x"
        return

    holder=two_in_tuple(board,2,4,6,"x")
    if holder[0] != -1 and holder[1]:
            board[holder[0]]="x"
            return
 #if the computer or player cannot win in one move,      
    if depth(board)!=-1:
        board[depth(board)]="x"
    else:
        for i in range(4):
            number=random.randrange(0, 9, 2)
            if board[number]!="x" and board[number]!="o":
                board[number]="x"
                return

        for i in range(4):
            number=random.randrange(1, 8, 2)
            if board[number]!="x" and board[number]!="o":
                board[number]="x"
                return

    
def num_of_wins(board):
    wins=0
    #check horizontal rows
    for i in range(0,7,3):
        holder=two_in_tuple(board,i,i+1,i+2, "x")
        if holder[0] != -1:
            wins+=1
            break
        
    #check vertical rows        
    for s in range(3):
        holder=two_in_tuple(board,s,s+3,s+6,"x")
        if holder[0] != -1:
            wins+=1
            break
        
    #check diagnals
    holder=two_in_tuple(board,0,4,8,"x")
    if holder[0] != -1 :
        wins+=1

        
    holder=two_in_tuple(board,2,4,6,"x")
    if holder[0] != -1:
        wins+=1

    return wins

def depth(board):
    dup=copy.deepcopy(board)
    holder=""
    #first tier move and second tier move
    fir=0
    sec=0
    #places "x" in all open spaces and checks how good each position is
    #searches for computer double two in rows
    for i in range(0,9):
        if dup[i]!="x" and dup[i]!="o":
            holder=dup[i]
            dup[i]="x"
        #if there are two "two in a rows" of "o" it fills with x
            if num_of_wins(dup)>=2:
                return i
            #favors results in the corner over in the edge
            elif num_of_wins(dup)==1 and (i==0 or i==2 or i==6 or i==8):
                fir=i
                dup[i]=holder
            elif num_of_wins(dup)==1:
               # sec=i
                dup[i]=holder
            else:
                dup[i]=holder
    #favors results in the corners

    #places "x" in all open spaces and checks how good each position is
    #blocks player's double two in rows
    for i in range(0,9):            
        if dup[i]!="x" and dup[i]!="o":
            holder=dup[i]
            dup[i]="o"
   #  if there are two "two in a rows" of "o" it fills with x
            if num_of_wins(dup)>=2 and (i==fir or i==sec):
                return i
            else:
                dup[i]=holder
    if fir!=0:
        return fir
    elif sec!=0:
        return sec
    return -1

        

    
def clickhandler(x, y):
    global count
    if do_user_move(the_board,x,y):
        draw_board(the_board)
        if not check_game_over(the_board):
           do_computer_move(the_board)
           draw_board(the_board)
           count+=1
           check_game_over(the_board)
           

def main():
    turtle.tracer(0,0)
    turtle.hideturtle()
    turtle.onscreenclick(clickhandler)
    draw_board(the_board)
    turtle.mainloop()

main()
