# CS606_ITC
This is our group project for **CS606 AI planning and decision making** based on the [2019 international university timetabling competition](https://www.itc2019.org/home). You can check out for the detail of this project in the [slides](https://github.com/WideSu/CS606_ITC/blob/main/documents/ITC_Presentation_Slides.pptx) and [report](https://github.com/WideSu/CS606_ITC/blob/main/documents/G4_MIP%20and%20CP%20for%20ITC%20problem.pdf)

# 1. Introduction
The university timetabling is a classical combinatorial optimization problem that takes a large number of variables and constraints into account. Student allocating and class scheduling decisions need to be made jointly against the backdrop of classroom and timeslot penalty and subject to practical rules. We model this problem as a two-stage mixed integer program which search for a feasible solution at the start and graduately improve from it iteratively, which reduced the time to get optimal solution by 58\%. Besides, we used a constraint programming method with the same objective function and constraints and compared the results for the two methods on 2019 ITC datasets. A comparison with results reported in this passage shows that the MIP approach outperformed the constraint programming approach in faster speed and better solution.

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

# Notebook Instructions 
Here is how you can run this:
1. Use `01_data_extraction.ipynb` to convert the dataset from xml format to python format
oconverting the dataset from .xml format to python format (lists & dictionary containers)
oXML files are located in Downloaded folder (raw data file downloaded from the ITC Competition website: ITC 2019: International Timetabling Competition 2019)
oSave Python format files are: dataset_01.py and dataset_04.py
Mixed Integer Programming
oFilename: 02_MIP.ipynb
orunning MIP model to solve and saving result to Solution folder as format sol_{dataset}_mp.py
oLog for each run is saved in Progress folder
Constraint Programming
oFilename: 03_CP.ipynb
oRunning CP model to solve and saving result to Solution folder with name formatted as sol_{dataset}_cp.py
Validation
oFilename: 04_validation.ipynb
oConverting python solution to xml competition format 
oSolution in xml format is in Solution/xml folder with name formatted as sol_{dataset}_{programming_type}.xml

