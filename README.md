# CS606_ITC
This is our group project for CS606 AI planning and decision making based on the 2019 international university timetabling competition. You can check out for the detail of this project in the [slides](https://github.com/WideSu/CS606_ITC/blob/main/ITC_Presentation_Slides.pptx) and [report](https://github.com/WideSu/CS606_ITC/blob/main/G4_MIP%20and%20CP%20for%20ITC%20problem.pdf) 

# 1. Introduction
Educational timetabling is an ongoing challenging administrative task that is required in most academic institutions. This is mainly due to a large number of constraints and requirements that have to be satisfied. Educational timetabling problems have been classified as NP-hard problems and can be divided into three types: exam timetabling, course timetabling and high school timetabling.

The domain of high school timetabling is not well developed when compared to other fields of educational timetabling such exam timetabling and high-school timetabling.

# 2. Problem Definition and Assumptions
The problem consists of university courses and student course requests. <br>
Our goal is to **find a proper time, a room and students for all the classes.**
<p align="center">
    <img width="575" alt="image" src="https://user-images.githubusercontent.com/44923423/161932477-52f6e811-ac17-43ad-b348-6bfebaaede6c.png">
</p>

# 3. Related work
Mixed integer programming, Heuristics, GA

# 4. Our model
<p align="center">
  <img width="462" alt="image" src="https://user-images.githubusercontent.com/44923423/161933180-5c9e6aea-3e3d-455f-a5b5-042dd43cf244.png">
</p>
    
## 4.1 MIP
### Decision variables
<p align="center">
<img width="435" alt="image" src="https://user-images.githubusercontent.com/44923423/161933328-8fb6f1dd-1fee-4075-90e2-bd849f071ae0.png">
</p>

### Objective function
<p align="center">
<img width="468" alt="image" src="https://user-images.githubusercontent.com/44923423/161933480-b7e24001-ac20-4087-9c98-89a9b9af6a3e.png">
</p>
### Constraints

- H1: Every class must be assigned a time
- H2: Every class must be assigned a room 
- H3: Every student must attend exactly one class for each subpart that he/she must attend
- H4: Prerequisite: Ex: If you take AI Planning – you must take Algorithm as well
- H5: The capacity limit of each class must not be exceeded.
- H6: A room cannot be used when it is unavailable
- H7: The pairs of classes in SameAttendees should not overlap in time Ex: Prof Dai is teaching Algorithm & Applied ML – these 2 classes cannot happen at the same time
- H8: Two classes can’t be at the same time and the same room
- 
## 4.2 CP
### Decision variables
<p align="center">
<img width="711" alt="image" src="https://user-images.githubusercontent.com/44923423/161934245-ab555d8d-f946-413e-aec8-b5d90a479dd3.png">
</p>
### Objective function
<p align="center">
<img width="227" alt="image" src="https://user-images.githubusercontent.com/44923423/161934391-1e3d2b9f-3be0-4430-8ed5-b8bbbc559af7.png">
</p>
### Constraints
<p align="center">
<img width="708" alt="image" src="https://user-images.githubusercontent.com/44923423/161934549-f137b76d-2135-461c-a05f-b7d89cc3f846.png">
</p>
