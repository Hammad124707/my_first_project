# my_first_project
import pandas as pd
def cf(game_length,results) :
     cnt = 0
     for i in range(game_length):
          if results[i] == "LOST":
               cnt +=1
     if game_length == 1:
      if cnt == 1:
          final_result = "LOST"
      else :
          final_result = "Win"        
     elif game_length == 3 :
      if cnt >= 2 :
          final_result = "LOST"
      else :
          final_result = "Win"        
     elif game_length == 5 :
      if cnt >=3 :
          final_result = "LOST"
      else :
          final_result = "Win"           

     return final_result     
               
temp_list = []
def entering_data(temp_list, count) : 
        played_against = input(f"Name of your  opponent #No {count} ")
        place = input("Played inside or outside ? ")
        game_length = int(input("Did you play best of 1 , 3 or 5 ? "))
        #match_result = input("did you win the match or lost? ") 
        results = [None] * game_length
        score = [None] * game_length
        for j in range(game_length):
            each_result = input(f"enter result whether you won or lost Set NO{j+1} ")
            each_result = each_result.upper()
            results.insert(j,each_result)
            each_score = input(f"Enter score for Set No{j+1} in the form of  [YourScore : OppScore]")
            score.insert(j,each_score)
        played_against = played_against.upper()
        place = place.upper()
        fR = cf(game_length,results)
#we have here created a list of dictionaries
        if game_length == 5:
            
            a1 = [{"Opponent" : played_against,"Place":place,"Best Of":game_length,"SET 01":results[0] +score[0],"SET 02":results[1] + score[1],"SET 03" : results[2] + score[2],"SET 04": results[3] + score[3],"SET 05":results[4] + score[4], "RESULT": fR}]
            temp_list += a1
        elif game_length == 3:
            a1 = [{"Opponent" : played_against,"Place":place,"Best_of":game_length,"SET 01":results[0] +score[0],"SET 02":results[1] + score[1],"SET 03" : results[2] + score[2],"RESULT" : fR}]
            temp_list += a1
        elif game_length == 1 :
            a1 = [{"Opponent" : played_against,"Place":place,"Best_of":game_length,"SET 01":results[0] +score[0],"RESULT": fR}] 
            temp_list += a1   
        #return temp_list
num_of_matches = int(input("Hi there, how many matches did you play today? "))
count = 1;
for j in range(num_of_matches):
    entering_data(temp_list,count)
    count += 1
df = pd.DataFrame.from_dict(temp_list)
print(df)
