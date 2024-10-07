# Ex.No: 8  Logic Programming –  Medical Diagnosis Expert System
### DATE:                                                                          
### REGISTER NUMBER :
### AIM: 
Write a Prolog program to build a medical Diagnosis Expert System.
###  Algorithm:
1. Start the program.
2. Write the rules for each diseases.
3. If patient have mumps then symptoms are fever and swollen glands.
4. If patient have cough, sneeze and running nose then disease is measles.
5. if patient have symptoms headache ,sneezing ,sore_throat, runny_nose and  chills then disease is common cold.
6. Define rules for all disease.
7. Call the predicates and Collect the symptoms of Patient and give the hypothesis of disease.
        

### Program:
```
symptoms(mumps, [fever, swollen_glands]).
symptoms(measles, [cough, sneeze, running_nose]).
symptoms(common_cold, [headache, sneezing, sore_throat, runny_nose, chills]).

diagnose(Disease, Symptoms) :-
    symptoms(Disease, DiseaseSymptoms),
    subset(DiseaseSymptoms, Symptoms).

start :-
    write('Welcome to the Medical Diagnosis Expert System.'), nl,
    write('Please enter the symptoms the patient is experiencing: '), nl,
    write('Available symptoms: [fever, swollen_glands, cough, sneeze, running_nose, headache, sore_throat, chills]'), nl,
    read(Symptoms),
    diagnose(Disease, Symptoms),
    write('The patient might have '), write(Disease), write('.'), nl.

```








### Output:
![image](https://github.com/Vasanth1234567/AI_Lab_2023-24/assets/86919099/6f9becde-04a3-4167-b19f-b067b946275c)



### Result:
Thus the simple medical diagnosis system was built sucessfully.
