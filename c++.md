## 类&对象

```c++
/*修饰*/
	
class Box{
    protected: //在派生类有作用
        int width;
};
class SmallBox:Box{
    private :
    int GetWidth(void){
        return width;
    }
    public:
    int heigth; 
}
```

```c++
/*构造函数*/
class STU{
    public:
    	int x,y,z;
    STU(int given_x,int given_y,int given_z);
    ~STU();
}
STU::STU(int given_x,int given_y,int given_z):x(given_x),y(given_y){
    z = given_z;
/*拷贝构造函数*/
#include<iostream>

using namespace std;

class line{
        public:
            line(int lenth);
            line(line &mom_obj);
            int print_the_lenth(void);
        private:
            int len;
};

int main(){
    //方法1
    /* line line1(3);
    line line2(line1);
    line2.print_the_lenth(); */
    //方法2
    line line1(3);
    line line2 = line1;
    line2.print_the_lenth();
}

line::line(int lenth){
    len = lenth;
    //如果形式参数也为len则需要
    //line::line(int len):len(len);
    cout << "using the class line";
}
line::line(line &mom_obj){
    len = mom_obj.len;
}
int line::print_the_lenth(void){
    cout << len;
}
    
/*友元函数*/
int number;
 class student{
     public:
     student(int score):score(score);
     friend class tearcher;
     friend void print_the_number(student stu);
     void print_the_score();
     private:
     int score;
 };
    void print_the_number(student stu){
        number += ~~(stu.score/90);
    }
  //不过是有对类中的protected和private有访问权罢了  

  /*内联函数*/
    //空间换时间
    inline int max(int a,int b)；



```

```C++
/*this*/
class line{
    public:
        line(int len);
        line(line &mom_obj);
        bool compare(line &line);
        int print_the_lenth(void);
    private:
        int len;
};

int main(){
    line line1(2),line2(3);
    if(line1.compare(line2))
        cout << "line1 > line2";
    else cout << "no";


}
line::line(int len){
    this -> len = len;
}    
bool line::compare(line &line){
    return this -> len > line.len;
}//注意表明line厂家的compare函数

```

