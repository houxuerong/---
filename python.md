---
===
graph = [
    [('图形','矩形'),('length',10),('height',5)], #用长和高表示矩形
    [('图形','正方形'),('length',5),('height',5)],
    [[0,0],[10,0],[15,5],[5,5]], #用四点坐标表示平行四边形
    [('三角形','直角'),('a',6),('b',8),('c',10)], #用三边边长表示三角形
    [('三角形','等边'),('a',6),('b',6),('c',6)],
    [('三角形','不规则'),('a',4),('b',5),('c',6)],
    [('图形','圆形'),('r',5)], #用半径表示圆
    [('图形','椭圆'),('a',5),('b',10)] #用长半轴和短半轴表示椭圆
    ]

def area_juxing(): #矩形和正方形的面积
    s_j = 0.
    for i in range(2):
        n = dict(graph[i]) #转换为字典
        s_j += n["length"]*n["height"]
    return s_j

def area_pingxing(p): #平行四边形的面积
    s_p = 0.
    x,y = zip(*p) #迭代，把两个数组糅在一起
    s_p += (x[1]-x[0])*(y[3]-y[1])
    return s_p

import math #导入数学模块
def area_san(): #三角形的面积
    s_s = 0.
    for i in range(3,5):
        n = dict(graph[i])
        p = (n["a"]+n["b"]+n["c"])/2. #已知三边，用海伦公式求面积
        s_s += math.sqrt(p*(p-n["a"])*(p-n["b"])*(p-n["c"]))
    return s_s

def area_yuan(): #圆形面积
    s_y = 0.
    n = dict(graph[6])
    s_y += 3.14*(n["r"]**2)
    return s_y

def area_tuo(): #椭圆面积
    s_t = 0.
    n = dict(graph[7])
    s_t += 3.14*n["a"]*n["b"]
    return s_t

area_zong = area_juxing() + area_pingxing(graph[2]) + area_san() + area_yuan() + area_tuo() #求总面积
print "总面积是：%s" %(area_zong)
print "平均面积是：%s" %(area_zong/len(graph)) #求平均面积

