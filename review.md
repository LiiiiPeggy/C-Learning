# C++ ��ĩ��ϰ���� 20210701

## Ŀ¼

1. [�ַ�����ָ��](#1)
   
2. [ָ���뺯��](#2)
3. [�ṹ�����б�](#3)
4. [�ļ�����](#4)
5. [��Ļ�������](#5)
6. [��ĸ߼�����](#6)
7. [��ļ̳С���̬���麯��](#7)
8. [�쳣����](#8)
9. [��׼ģ��STL](#9)
    
---

## <span id="1">1 �ַ�����ָ��</span>

### 1.1 �����ַ����ַ���

* ���ַ����ĳ���
  <pre name = "code" class = "c++">
  char name[10] = {'T', 'o', 'm', '\0', 'P', 'e', 't', 'e', 'r', '\0'};
  cout << strlen(name) << sizeof(name) << endl; 
  </pre>
  ע�⣺���ַ�������ʱ����'\0'�ͻ����

* �ַ����Ŀ���
  
  **��ʽһ**
  <pre name = "code" class = "c++">
  char* strcpy(char s1[], char s2[])
  </pre>
  ����
  <pre name = "code' class = "c++">
  char src[80] = {"I am a student"};
  char dst[80];
  strcpy(dst,. src);
  </pre>
  ע�⣺����ʹ�á�=���Ž���ֱ�Ӹ�ֵ

  **��ʽ��**
  <pre name = "code" class = "c++">
  char* strncoy(char s1[], const char s2[], int len)
  </pre>
  ����
  <pre name = "code" class = "c++">
  char src[80] = {"I am a student"};
  char dst[80];
  strncpy(dst,. src);
  dst[10] = '\0';
  </pre>
  ע�⣺�������'\0'�ַ���������־

* �ַ���������
  <pre name = "code" class = "c++">
  char* strcat(char s1[], const char s2[], int len)
  </pre>
  ��s2�ַ������ӵ�s1��β�����޸���s1�����ص���s1���׵�ַ

  ע�⣺s1�Ŀռ�Ҫ�㹻��
  
  ���磺
  <pre name = "code" class = "c++">
  char s1[20] = "You";
  char s2[20] = "&Me";
  strcat(s1, s2);
  </pre>

* �ַ����ıȽ�
  
  **��ʽһ**
  <pre name = "code" class = "c++">
  int strcmp(const char s1[], const char s2[])
  </pre>
  �Ƚ������ַ����Ĵ�С�����Ǵ���������Ƚ϶�Ӧ�ַ���ASCII��

  ��s1 > s2���򷵻�1

  ��s1 < s2���򷵻�-1

  ��s1 = s2���򷵻�0

  **��ʽ��**
  <pre name = "code" class = "c++">
  int strncmp(const char s1[], const s2[], int len)
  </pre>
  �Ƚ������ַ�����ǰlen���ַ������ַ���s1����s2�ĳ���С��len������strcmp����

  ���磺
  <pre name = "code" class = "c++">
  char s1[10] = "China";
  char s2[10] = "Chinese";
  cout << strncmp(s1, s2, 5) << endl;//������Ϊ-1
  </pre>

* �ַ����Ĵ�Сдת��
  
  **��д��Сд**
  <pre name = "code" class = "c++">
  char* strlwr(char s[])
  </pre>
  **Сд���д**
  <pre name = "code" class = "c++">
  char* strupr(char s[])
  </pre>

* �ַ������Ӵ�����
  <pre name = "code" class = "c++">
  char* strstr(const char s1[], const char s2[])
  </pre>
  ����ַ���s1����Ҫ���ҵ��Ӵ�s2���򷵻�s1��s1�е�һ�γ��ֵĵ�ַ������ֱ�ӷ���NULL

* �ַ���ת��Ϊ�����ĺ���
  <pre name = "code" class = "c++">
  int atoi(const char str[])
  </pre>
  ���磺
  <pre name = "code" class = "c++">
  char s1[80] = "789123",
  s2[80] = "789X123",
  s3[80] = "X123";
  int i = atoi(s1);//789123
  int j = atoi(s2);//789
  int k = atoi(s3);//0
  </pre>
  ת���ɱ���������;��Լ������

  atof��atod...

* ����ת��Ϊ�ַ���
  <pre name = "code" class = "c++">
  char* itoa(int value, char str[], int radix)
  </pre>
  ���磺
  <pre name = "code" class = "c++">
  int n = 123;
  char s1[20], s2[20];
  itoa(n, s1, 3);//����3����
  itoa(n, s2, 10);//����10����
  </pre>

### 1.2 ��׼C++��String��

* ������ͷ�ļ�
  <pre name = "code" class = "c++">
  string
  </pre>

* ��ȡ����
  <pre name = "code" class = "c++">
  string name;
  getline(cin, name);
  </pre>
  ע�⣺Ҫ��char����������
  <pre name = "code" class = "c++">
  char name[10];
  gets(name);
  cin.get(name, 10);
  cin.getline(name, 10);
  </pre>

* string����ıȽ�
  string����Ҳ�������ַ����Ƚϣ�����
  <pre name = "code" class = "c++">
  string name1 = "John";
  char name2[10] = "Jone";
  cout << (name1 > name2);//0
  cout << (name1 < name2);//1
  cout << (name1 == name2);//0
  </pre>

* string����ĳ�ʼ��
  <pre name = "code" class = "c++">
  string test1;    //�մ�
  string test2 = "����"; //ʹ��=
  string test3("����");   //ʹ�������ַ�������Ϊ�����������캯��
  string test4(test2); //��һ��string��ʼ����һ��string
  string test5(test2,pos,num); //��test2�еĵ�pos��λ�ÿ�ʼ����������Ϊnum���ַ�
  string test6 = test2 + "����" + test3 //��ϳ�ʼ��
  string test7 = test2.substr(pos,num); //��test2�еĵ�pos��λ�ÿ�ʼ����������Ϊnum���ַ�
  string test8 = test2.substr(); //�����б�Ϊ����´��test2���������󣨸���test2�ļ�㷽����
  string test9(num,ch); //����num���ַ���ch��test9
  </pre>

* string���ͳ��õĲ�����
  <pre name = "code" class = "c++">
  =, assign() //������ֵ
  swap() //���������ַ���������
  +=, append(), push_back() //��β������ַ�
  insert() //�����ַ�
  erase() //ɾ���ַ�
  clear() //ɾ��ȫ���ַ�
  replace() //�滻�ַ�
  + //�����ַ���
  ==, !=, <, <=, >, >=, compare() //�Ƚ��ַ���
  size(), length() //�����ַ�����
  max_size() //�����ַ��Ŀ���������
  empty() //�ж��ַ����Ƿ�Ϊ��
  capacity() //�������·���֮ǰ���ַ�����
  reserve() //����һ�����ڴ�������һ���������ַ�
  [ ], at() //��ȡ��һ�ַ�
  >>,getline() //��stream��ȡĳֵ
  << //��ıֵд��stream
  copy() //��ĳֵ��ֵΪһ��C_string
  c_str() //��������C_string����
  data() //���������ַ�������ʽ����
  substr() //����ĳ�����ַ���
  find() //�����ַ�
  begin() end() //�ṩ����STL�ĵ�����֧��
  rbegin() rend() //���������
  get_allocator() //����������
  </pre>

### 1.3 ָ��ĸ��ָ������Ķ����ʹ��

* ָ��������Ǵ�ŵ�ַ�ı���
  
* ����ָ�����
  ���磺
  <pre name = "code" class = "c++">
  int* pInt;
  </pre>
  ע�⣺
   
    * ָ�벻֪���ڴ��0�ŵ�Ԫ����ָ�����ֵΪ0����NULL�����ʾ��ָ��
  
    * ��ֵַ��������ֵ��ͬ

    * ���ۺ������͵�ָ�붼ռ��4���ֽڵ��ڴ�ռ�
  

* �����*��&
  
  *��ͨ��ָ�������ָ��������ֵ

  &������ָ���ڴ���ĵ�ַ

* ����ָ�����
  <pre name = "code" class = "c++">
  int x = 30, y = 90;
  int *p1 = &x, *p2 = &y, t;
  t = *p1;
  *p1 = *p2;
  *p2 = t;
  </pre>
  ��������ʵ����p1��p2ָ�������ֵ�Ľ���

### 1.4 ָ��������

* ��������ķ�ʽ
  
  * �±���ʽ
  
  * ָ����ʽ

* ������������

  * ȫ������;�̬���飺�ھ�̬�������б�����
  
  * �ֲ���������ջ�ϱ�����

* ��������Ӧһ���ڴ棬���ַ�������������������ڱ��ֲ��䣬ֻ����������ݿ��Ըı�
* ָ�����ָ���������͵��ڴ�飬�������ǡ��ɱ䡱
* ָ��һά����Ԫ�ص�ָ��
  
  ���������������Ŀ�ʼ��ַ����������ʱһ��ָ�볣��������
  <pre name = "code" class = "c++">
  int a[10], *p;
  p = a;
  p = &a[0];//���ߵȼ�
  </pre>

* ָ��Ƚ�

  ָ��ͬһ�����������ָ����Խ��бȽ�

  �����ŵĴ���
  <pre name = "code" class = "c++">
  for(p1 = set, p2 = set+length-1; p1 < p2; p1++, p2--) {
    t = *p1;
    *p1 = *p2;
    *p2 = t;
  }
  </pre>

* ָ�����֮��ļӷ�������

* ָ���ά����Ԫ�ص�ָ��
  
  ��ά����Ԫ��a[i][j]�ı�ʾ
  <pre name = "code" class = "c++">
  //��ʾ��ַ
  &a[i][j]
  a[i]+j
  *(a+i)+j
  
  //��ʾ��ֵ
  a[i][j]
  \*(a[i]+j)
  \*(\*(a+i)+j)
  (\*(a+i))[j]
  </pre>
  ע�⣺a[0] == a[0][0]

  һ��ͨ�õĶ�ά������������
  <pre name = "code" class = "c++">
  void Print(int* p, int row, int col) {
    int i;
    for(i = 0; i < row*col; i++, p++) {
      if(i % col == 0) {
        cout << end;
      }
      cout << setw(4) << *p;
    }
    cout << endl;
  }
  </pre>

---

## <span id="2">2 ָ���뺯��</span>

### 2.1 �����Ĵ��ݷ�ʽ

* �������͵ı����������β�
  
  ��������x��y��ֵ�����û������͵ı����������β�
  <pre name = "code" class = "c++">
  void swap(int a, int b) {
    int t;
    t = a;
    a = b;
    b = t;
  }
  </pre>
  ���ǵ����ֵ���ݣ��βεı仯����Ӱ��ʵ��

* ����������Ϊ�����β�

  ��������x��y��ֵ�����������������������β�
  <pre name = "code" class = "c++">
  void swap(int& a, int& b) {
    int t;
    t = a;
    a = b;
    b = t;
  }
  </pre>
  ͨ�����屻�����еĲ���Ϊ�������ͣ�������������ֵ�ı�

* ָ��������Ϊ�����β�

  ��������x��y��ֵ������ָ�������������β�
  <pre name = "code" class = "c++">
  void swap(int* px, int* py) {
    int t;
    t = *px;
    *px = *py;
    *py = t;
  }
  </pre>
  ͨ�����屻���ú����еĲ���Ϊָ�����ͣ�ͨ����Ӵ�ȡ������������ֵ�ı�

  ע�⣺ָ�������������βε���һ����ʽ������������������

### 2.2 ����ָ��ĺ�����ָ������ָ��

* ָ���ͺ���
  
  һ�������ķ���ֵ��ĳ���������͵ĵ�ֵַ����ָ���ͺ���
  <pre name = "code" class = "c++">
  int* function(int x, int y) {
    return x+y;
  }
  </pre>

* ����ָ��
  
  ��������ڵ�ַ������ָ���������ָ������ڵ�ַ�ı�����
  <pre name = "code" class = "c++">
  int (*fun)(int , int);
  int max(int x, int y) {
    return x > y?x : y;
  }
  fun = max;
  </pre>
  �÷�ʾ��
  <pre name = "code" class = "c++">
  int process(int x, int y, int (*fun)(int, int)) {
    return fun(x, y);
  }
  </pre>

### 2.3 ָ��������ָ��ָ���ָ��

* ָ������
  
  һ�������������е�Ԫ�ض���ָ�������Ϊָ������

* ָ������������ָ��ı����������*��[]�����ȼ�˳��ͬ

  <pre name = "code" class = "c++">
  int (*p)[M]; //p��һ������ָ�룬һ����ָ�룬ָ��ӵ��M��Ԫ�ص�һά����
  int* p[M]; //p��һ��ָ�����飬������M��ָ��
  </pre>

* main�����Ĳ���
  
  ��main()����ͷ�������ĸ�ʽΪ
  <pre name = "code" class = "c++">
  int main(int argc, char* argv[])
  int main(int argc, char** argv)
  //argc��ʾ���������ַ����ĸ���
  //argv[]ָ���������еĸ����ַ���
  </pre>
  �ٸ����ӣ�ͨ�������в��������������ݵĺ�
  <pre name = "code" class = "c++">
  int main(int argc, char* argv[]) {
    int sum, i;
    cout << "Command name:" << argv[0] << endl;
    for(sum = 0, i = 1; i < argc; i++) {
      sum += atoi(argv[i]);
    }
    cout << "Sum is:" << sum << endl;
  }
  </pre>

* ָ��ָ���ָ��
  
  �ٸ�����
  <pre name = "code" class = "c++">
  int x, *p = &x, **pp = p;
  </pre>

### 2.4 �ڴ�Ķ�̬�������ͷ�

* �����洢�ռ�ķ�����ϵͳ��ɵģ������û���Ԥ
  
  * ��̬����������ʱ����ռ�
  
  * ��̬������ϵͳ�˶�ʱ����ռ�

* ����̬����ռ������û��ڱ��ʱ���ŵ�
* ������ٿռ�������ʱ���������һ��ͨ��ָ����ʿռ�
* new���ڶ�̬���봢��ռ䣬delete�����ͷ�new����Ĵ洢�ռ�
  <pre name = "code" class "c++">
  //���䵥��Ԫ�ؿռ�
  int* iptr;
  iptr = new int;
  *iptr = 25;
  //Ҳ��������
  iptr = new int(25);
  delete iptr;
  //����һƬ�����Ŀռ�
  int* a;
  a = new int[100];
  delete []a;
  </pre>
  ע�⣺��������Ĳ�����һ��ָ�룬��Ҫ��ָ��ȥ���붯̬�ڴ棬�������Ϊ����Ŀռ��޷��ͷŶ�����ڴ�й©

### 2.5 void �� const ����ָ�����

#### 2.5.1 void����ָ�����

* void����ָ��
  
  void����ָ�������һ�ֲ�ȷ�����͵�ָ��

* �κ����͵�ָ�붼����ֱ�Ӹ���������������ת��

  <pre name = "code" class = "c++">
  void* p1;
  int* p2;
  p1 = p2;
  </pre>

* ���ܶ�voidָ�������������

#### 2.5.2 const����ָ�����
  
* ָ������ָ��
  
  ���Ըı�ָ����ָ�Ŀռ䣬��������ͨ��ָ��ı�������ָ������

  <pre name = "code" class = "c++">
  int i = 6;
  const int* p1 = &i;
  const int m = 16;
  *p1 = 16; //wrong
  p1 = &m; //true
  </pre>

* ����ָ��

  ���Ըı�ָ����ָ��ռ��е����ݣ����ǲ��ܸı�ָ���ָ��

  <pre name = "code" class = "c++">
  char stringA[10] = "abcd", stringB[10] = "xyz";
  char* const sp = atringA;
  sp = stringB; //wrong
  *(sp+1) = 't'; //true
  </pre>

* ָ������ָ�볣��

  �Ȳ������޸�ָ����ָ�������ֲ��ɸı�ָ���ָ��

---

## <span id="3">3 �ṹ�����б�</span>



---

## <span id="4">4 �ļ�����</span>

---

## <span id="5">5 ��Ļ�������</span>

---

## <span id="6">6 ��ĸ߼�����</span>

---

## <span id="7">7 ��ļ̳С���̬���麯��</span>

---

## <span id="8">8 �쳣����</span>

---

## <span id="9">9 ��׼ģ��STL</span>

