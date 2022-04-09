```cpp
//sample.cpp
class Knight{ 
    public:
        void Move(int y, int x);
        void Attack();
        void Die();
    
    public:
        int _attack;
        int _hp;
        int _posY;
        int _posX;
};


void Knight::Die(){
    _hp = 0;    
}


int main(){
    Knight k1;
    k1._hp = 100;
    k1._attack = 10;
    k1._posY = 2;
    k1._posX = 2;
    Knight k1;
    
    k1.Die();

    return 0;    
}


```



![](C:\Users\rohfr\AppData\Roaming\marktext\images\2022-04-08-17-48-35-image.png)

위는 sample.c를 실행했을 때 생성된 어셈블리 코드의 일부이다. 이 코드를 확인해보면 컴퓨터가 어떠한 방식으로 멤버 변수의 값을 바꾸는지 볼 수 있다.

위의 어셈블리는 _hp를 0으로 세팅하는데 아래와 같이 작동함을 확인할 수 있다.

 

    1. eax 레지스터에 this의 주소를 넣고

    2. 거기서 4byte 만큼 떨어진 곳에 double word 0을 넣는다.



[eax+4] 에서 4를 더한 것은 멤버 변수는 아래와 같이 메모리에 들어가 있기 때문이다. Knight 클래스 멤버 변수는 모두 int고 그 중 두번째로 _hp가 선언되어 있다. this는 객체에 대한 포인터고 첫번째 멤버 변수를 가리키고 있다. 따라서 그곳에서 4 byte 떨어진 주소에 _hp가 있으므로 그 위치에 0을 쓰도록 하는 것이다.

| address   | Member variable |
| --------- |:---------------:|
| this      | _attack         |
| this + 4  | _hp             |
| this + 8  | _posY           |
| this + 23 | _posX           |

![](C:\Users\rohfr\AppData\Roaming\marktext\images\2022-04-09-08-46-20-image.png)

![](C:\Users\rohfr\AppData\Roaming\marktext\images\2022-04-09-08-59-39-image.png)

_hp가 0으로 잘 세팅이 된 것을 볼 수 있다. 참고로 메모리 주소창에 &k1을 치면 this와 동일한 주소 (여기서는 0x0049FBA4)가 나옴을 확인할 수 있다.


