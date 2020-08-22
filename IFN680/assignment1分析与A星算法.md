# Assignment1 

+ search.py  
1. def memoize  
记录数值，如果已经有值，则返回值。没有值，则写入。
2. class Queue  
一个抽象队列
3. def LIFOQueue  
栈
4. class FIFOQueue  
队列
5. class PriorityQueue  
优先队列。内部是堆
+ sokoban.py
1. def find_1D_iterator
2. def find_2D_iterator
3. class Warehouse  
仓库的初始位置
+ mySokobanSolver.py  
唯一要提交的文件
1. def my_team()  
团队成员
2. def taboo_cells(warehouse)  
定义禁忌单元格。2种定义方法：  
1- 所有角落  
2- 沿着墙的2个角落之间的一排格子，而且那一排里没有终点
3. class SokobanPuzzle  
负责解决问题：推箱子的地图。  
一个类，负责记录地图状态，包括初始值，目前的箱子和人的位置，以及计算路径。
4. def check_elem_action_seq  
检查一系列操作在目标地图中是否合法  
如果不合法，返回字符串"impossible"
如果可以，返回处理过后的地图，格式参见sokoban.py-Warehouse-def __str __ (self)
5. def solve_sokoban_elem(warehouse)  
解决问题单元，输入地图，输出一个列表，包括[上，下，左，右]  
问题单元指的是单次移动
6. def can_go_there  
输入一个坐标，输出人是否可以移动到当前坐标的位置  
但是不会移动，仅仅是判断  
7. solve_sokoban_macro  
解决一整个问题，指的是从地图开始到解决问题的全部流程
8. solve_weighted_sokoban_elem   
计算解决问题的比重。其实就是要求最短路径。这里会加入所有解决方案的路径进行思考，比较，找出最优解。针对的是单次移动。

# A*算法