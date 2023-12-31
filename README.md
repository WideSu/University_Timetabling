# CS606_ITC
An AI planing project based on the [2019 international university timetabling competition](https://www.itc2019.org/home) which used commercial software IBM **CPLEX** to **generate feasible course timetables with minimum penalty**. 
Our contributions include:
1. Drawed few assumptions to make this competition problem doable in 4 weeks. 
2. Developed our own constraint programming, mixed integer programming models by modeling this problem as a two-stage mixed-integer program that searches for a feasible solution at the start and gradually improves from it iteratively, which reduced the time to get an optimal solution by 58%, showed comparison with results reported in this passage shows that the MIP approach outperformed the constraint programming approach in faster speed and better solutions.
3. Tested them on two datasets provided on ITC official website and compared the result.

You can check out for the detail of this project in the [slides](https://github.com/WideSu/CS606_ITC/blob/main/documents/ITC_Presentation_Slides.pdf) and [report](https://github.com/WideSu/CS606_ITC/blob/main/documents/G4_MIP%20and%20CP%20for%20ITC%20problem.pdf)

# Notebook Instructions 
Here is how you can run this:

Generally, there is 4 jupyter notebooks in the `Code` file.
1. Use [`01_data_extraction.ipynb`](https://github.com/WideSu/CS606_ITC/blob/main/Code/01_data_extraction.ipynb) to convert the raw_data(in data/raw_data) from xml format to python format. Note that those are sample data downloaded from ITC website. You can also download other instances via this [link](https://www.itc2019.org/instances/all) to test.
<p align="center">
<img width="600" alt="image" src="https://user-images.githubusercontent.com/44923423/161974394-2bc76c90-fcfc-4404-8fc1-29bbea20dc93.png">
</p>

2. Use the [`02_MIP.ipynb`](https://github.com/WideSu/CS606_ITC/blob/main/Code/02_MIP.ipynb) to run the mixed integer programming model.
3. Use the [`03_CP.ipynb`](https://github.com/WideSu/CS606_ITC/blob/main/Code/03_CP.ipynb) to run constraint programming model.

3. Use the [`04_validation.ipynb`](https://github.com/WideSu/CS606_ITC/blob/main/Code/04_validation.ipynb) to converting python solution to xml format which can be submitted on the portal of the competition. *Noted*: Solution in xml format is in Solution/xml folder with name formatted as sol_{dataset}_{programming_type}.xml

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
    
## 4.1 Mixed Integer Programming Model
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

## 4.2 Constraint Programming Model

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


