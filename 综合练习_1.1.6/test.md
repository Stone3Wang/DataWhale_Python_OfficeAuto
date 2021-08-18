```python
import os
import cities
import random
#os.getcwd()
#创建俩文件夹
#os.makedirs('E:\\Files\\wl_jupyter_notebook\\Datawhale_office_auto\\task01\\综合练习\\test')
#os.makedirs('E:\\Files\\wl_jupyter_notebook\\Datawhale_office_auto\\task01\\综合练习\\answer')
#cities.cities[0]
#print(wd)
```


```python
#创建测试34个txt文件
for i in range(34):
    random.shuffle(cities.cities)#每个txt文件都需先打乱字典内容顺序
    #分别打开新建的存放测试和答案文件夹
    file=open(os.path.join('E:\\Files\\wl_jupyter_notebook\\Datawhale_office_auto\\task01\\综合练习\\test',f'test{str(i+1)}.txt'),'w',encoding = 'utf-8')
    file_0 = open(os.path.join('E:\\Files\\wl_jupyter_notebook\\Datawhale_office_auto\\task01\\综合练习\\answer',f'answer{str(i+1)}.txt'),'w')
    for j in range(34):#每个txt文件写入34题
        cities_copy = cities.cities[:]#复制原字典
        #print(cities_copy)
        cities_copy.pop(j)#从复制的字典中弹出写入txt文件的字典键-值对，包含正确的答案值
        choices = random.sample(cities_copy,3)#从弹出后的字典中随机选三个键值对组成新的列表用于备选项
        choices.append(cities.cities[j])#从原字典中选择正确选项键值对加入新列表最后
        choices_copy = choices[:]#选项字典列表复制，每项为‘城市’：简称’
        random.shuffle(choices)#对选项字典列表打乱顺序
        #print(choices)
        alternatives = {}#新建一选项字典，并将打乱后的字典列表的值赋个每个字母键
        alternatives['A'] = choices[0]['简称']
        alternatives['B'] = choices[1]['简称']
        alternatives['C'] = choices[2]['简称']
        alternatives['D'] = choices[3]['简称']
        #写入测试卷txt文件
        file.write('第'+str(j+1)+'题.'+cities.cities[j]['城市']+'的简称是:'+'__'+'\n'+
                  'A.'+alternatives['A']+'\t'+'B.'+alternatives['B']+'\t'+'C.'+alternatives['C']+'\t'+'D.'+alternatives['D']+'\n')
        key_list =[]#针对选项字典新建分别对应于键和值的列表
        value_list = []
        for key,value in alternatives.items():#选项字典中键值分别赋给新建的两列表
            key_list.append(key)
            value_list.append(value)
        if choices_copy[3]['简称'] in value_list:#对原来选择出四项的字典列表，最后一项是包含正确答案
            answer = key_list[value_list.index(choices_copy[3]['简称'])]#从正确值所对应于value_list的索引找出选项字典对应的ABCD
        file_0.write('第'+str(j+1)+'题的答案是:'+answer+'\n')#写入答案文件中
        #print(answer)
        #print(alternatives)

    file.close()
#print(cities.cities)
```
