# -퍼지AI를 이용한 인슐린 투여량-
퍼지 인공지능을 이용하여 당화혈색소와 탄수화물 섭취량에 따른 인슐린 투여량을 계산해준다 
### 기대효과  
당화 혈색소와 탄수화물의 섭취량에 따라 당뇨환자가 간편하고 정확하게 자가 인슐린 투여량을 정할 수 있다.
------------------------------------------------------------
### INPUT
입력 1 : 탄수화물 섭취량 (단위 : g)     
입력 2 : 당화혈색소 (단위 : %) 

### OUTPUT
출력 : 인슐린 투여량 (단위 : 단위(unit))
--------------------------------------------------------------
### 입출력값을 이용한 추론 규칙
1. 당화혈색소가 낮으면 인슐린을 매우 적게 투여한다   
2. 탄수화물 섭취량이 적고 당화혈색소가 보통이면 인슐린을 매우 적게 투여한다   
3. 탄수화물 섭취량이 적고 당화혈색소가 높으면 인슐린을 보통만큼 투여한다   
4. 탄수화물 섭취량이 보통이고 당화혈색소가 정상이면 인슐린을 적게 투여한다   
5. 탄수화물 섭취량이 보통이고 당화혈색소가 높으면  인슐린을 보통만큼 투여한다   
6. 탄수화물 섭취량이 많고 당화혈색소가 정상이면 인슐린을 많이 투여한다   
7. 탄수화물 섭취량이 많고 당화혈색소가 높으면 인슐린을 매우 많이 투여한다   
-------------------------------------------------------------------------------------
### 퍼지 집합에 대한 소속함수   
##### 입력1 : 탄수화물(g)
|  탄수화물 섭취량  | 소속함수 |
| ------ | -- | 
| 적음 | 섭취량<10 | 
| 보통 | 10<=섭취량<=20  | 
| 많음 | 섭취량>20 |      

![입력1 소속함수](https://user-images.githubusercontent.com/105612931/172599935-d105b4c1-1a30-4c18-a742-71a95696a2f9.png)

##### 입력2 : 당화혈색소(%)
|  당화혈색소 수치  | 소속함수 |
| ------ | -- | 
| 정상 | 당화혈색소 <6   /  인슐린 투여량 = 투여안함 | 
| 높음 | 6<=당화혈색소<=8  | 
| 매우높음 | 당화혈색소 >8  |      

![입력2 소속함수](https://user-images.githubusercontent.com/105612931/172600211-8fb86783-d3c9-4ada-bc1b-03731322de85.png)

##### 출력 : 인슐린투여량
|  인슐린투여량  | 소속함수 |
| ------ | -- | 
| 매우적게투여 | 당화혈색소 =정상  /   탄수화물 섭취량 = 적음 and 당화혈색소 = 높음 | 
| 적게투여 | 탄수화물 섭취량=보통 and 당화혈색소 = 높음  | 
| 보통투여 | 탄수화물 섭취량=적음 and 당화혈색소 = 매우높음   /  탄수화물 섭취량=보통 and 당화혈색소 = 매우높음 | 
| 많이투여 | 탄수화물 섭취량=많음 and 당화혈색소 = 높음 | 
| 매우많이투여 |  탄수화물 섭취량=많음 and 당화혈색소 = 매우높음  |       

![출력 소속함수](https://user-images.githubusercontent.com/105612931/172599386-c2ed5f92-0729-41a8-980e-92ffd40c7646.png)

