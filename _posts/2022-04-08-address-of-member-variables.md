#C/C++ : this, 멤버 변수의 주소,  객체의 주소, 어셈블리 코드로 확인하기.

`class Knight { 

public:    

    void Move(int y, int x);
    void Attack();
    void Die();

public: // Data : Member variables
    int _attack;
    int _hp;
    int _posY;
    int _posX;
};`



![](C:\Users\rohfr\AppData\Roaming\marktext\images\2022-04-08-17-48-35-image.png)

| this      | _attack |
| --------- | ------- |
| this + 4  | _hp     |
| this + 8  | _posY   |
| this + 12 | -posX   |

위의 어셈블리는 _hp를 0으로 세팅하는 멤버 함수가 실행 되었을 때의 어셈블리 코드이다. 

    1.eax 레지스터에 this의 주소를 넣고

    2.거기서 4byte 만큼 떨어진 곳에 double word 0을 넣는다.



4를 더한 것은 Knight 클래스 멤버 변수가 모두 int이고 두번째로 선언된 변수가 _hp이기 때문이다.  this는 객체에 대한 포인터로 첫번째 멤버변수의 주소다. 따라서 그곳에서 4 byte 떨어진 주소에 _hp가 있다.  만약 _hp가 가장 앞에 선언되었으면

`eax, dword ptr [this]

dword ptr [eax], 0`

와 같이 어셈블리 코드가 생성 되었을 것이다.


