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
  ```cpp
  char name[10] = {'T', 'o', 'm', '\0', 'P', 'e', 't', 'e', 'r', '\0'};
  cout << strlen(name) << sizeof(name) << endl; 
  ```
  ע�⣺���ַ�������ʱ����'\0'�ͻ����

* �ַ����Ŀ���
  
  **��ʽһ**
  ```cpp
  char* strcpy(char s1[], char s2[])
  ```
  ����
  ```cpp
  char src[80] = {"I am a student"};
  char dst[80];
  strcpy(dst, src);
  ```
  ע�⣺����ʹ�á�=���Ž���ֱ�Ӹ�ֵ

  **��ʽ��**
  ```cpp
  char* strncpy(char s1[], const char s2[], int len)
  ```
  ����
  ```cpp
  char src[80] = {"I am a student"};
  char dst[80];
  strncpy(dst, src, 10);
  dst[10] = '\0';
  ```
  ע�⣺�������'\0'�ַ���������־

* �ַ���������
  ```cpp
  char* strcat(char s1[], const char s2[], int len)
  ```
  ��s2�ַ������ӵ�s1��β�����޸���s1�����ص���s1���׵�ַ

  ע�⣺s1�Ŀռ�Ҫ�㹻��
  
  ���磺
  ```cpp
  char s1[20] = "You";
  char s2[20] = "&Me";
  strcat(s1, s2);
  ```

* �ַ����ıȽ�
  
  **��ʽһ**
  ```cpp
  int strcmp(const char s1[], const char s2[])
  ```
  �Ƚ������ַ����Ĵ�С�����Ǵ���������Ƚ϶�Ӧ�ַ���ASCII��

  ��s1 > s2���򷵻�1

  ��s1 < s2���򷵻�-1

  ��s1 = s2���򷵻�0

  **��ʽ��**
  ```cpp
  int strncmp(const char s1[], const s2[], int len)
  ```
  �Ƚ������ַ�����ǰlen���ַ������ַ���s1����s2�ĳ���С��len������strcmp����

  ���磺
  ```cpp
  char s1[10] = "China";
  char s2[10] = "Chinese";
  cout << strncmp(s1, s2, 5) << endl;//������Ϊ-1
  ```

* �ַ����Ĵ�Сдת��
  
  **��д��Сд**
  ```cpp
  char* strlwr(char s[])
  ```
  **Сд���д**
  ```cpp
  char* strupr(char s[])
  ```

* �ַ������Ӵ�����
  ```cpp
  char* strstr(const char s1[], const char s2[])
  ```
  ����ַ���s1����Ҫ���ҵ��Ӵ�s2���򷵻�s1��s1�е�һ�γ��ֵĵ�ַ������ֱ�ӷ���NULL

* �ַ���ת��Ϊ�����ĺ���
  ```cpp
  int atoi(const char str[])
  ```
  ���磺
  ```cpp
  char s1[80] = "789123",
  s2[80] = "789X123",
  s3[80] = "X123";
  int i = atoi(s1);//789123
  int j = atoi(s2);//789
  int k = atoi(s3);//0
  ```
  ת���ɱ���������;��Լ������

  atof��atod...

* ����ת��Ϊ�ַ���
  ```cpp
  char* itoa(int value, char str[], int radix)
  ```
  ���磺
  ```cpp
  int n = 123;
  char s1[20], s2[20];
  itoa(n, s1, 3);//����3����
  itoa(n, s2, 10);//����10����
  ```

### 1.2 ��׼C++��String��

* ������ͷ�ļ�
  ```cpp
  string
  ```

* ��ȡ����
  ```cpp
  string name;
  getline(cin, name);
  ```
  ע�⣺Ҫ��char����������
  ```cpp
  char name[10];
  gets(name);
  cin.get(name, 10);
  cin.getline(name, 10);
  ```

* string����ıȽ�
  string����Ҳ�������ַ����Ƚϣ�����
  ```cpp
  string name1 = "John";
  char name2[10] = "Jone";
  cout << (name1 > name2);//0
  cout << (name1 < name2);//1
  cout << (name1 == name2);//0
  ```

* string����ĳ�ʼ��
  ```cpp
  string test1;    //�մ�
  string test2 = "����"; //ʹ��=
  string test3("����");   //ʹ�������ַ�������Ϊ�����������캯��
  string test4(test2); //��һ��string��ʼ����һ��string
  string test5(test2,pos,num); //��test2�еĵ�pos��λ�ÿ�ʼ����������Ϊnum���ַ�
  string test6 = test2 + "����" + test3 //��ϳ�ʼ��
  string test7 = test2.substr(pos,num); //��test2�еĵ�pos��λ�ÿ�ʼ����������Ϊnum���ַ�
  string test8 = test2.substr(); //�����б�Ϊ����´��test2���������󣨸���test2�ļ�㷽����
  string test9(num,ch); //����num���ַ���ch��test9
  ```

* string���ͳ��õĲ�����
  ```cpp
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
  ```

### 1.3 ָ��ĸ��ָ������Ķ����ʹ��

* ָ��������Ǵ�ŵ�ַ�ı���
  
* ����ָ�����
  ���磺
  ```cpp
  int* pInt;
  ```
  ע�⣺
   
    * ָ�벻֪���ڴ��0�ŵ�Ԫ����ָ�����ֵΪ0����NULL�����ʾ��ָ��
  
    * ��ֵַ��������ֵ��ͬ

    * ���ۺ������͵�ָ�붼ռ��4���ֽڵ��ڴ�ռ�
  

* �����*��&
  
  *��ͨ��ָ�������ָ��������ֵ

  &������ָ���ڴ���ĵ�ַ

* ����ָ�����
  ```cpp
  int x = 30, y = 90;
  int *p1 = &x, *p2 = &y, t;
  t = *p1;
  *p1 = *p2;
  *p2 = t;
  ```
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
  ```cpp
  int a[10], *p;
  p = a;
  p = &a[0];//���ߵȼ�
  ```

* ָ��Ƚ�

  ָ��ͬһ�����������ָ����Խ��бȽ�

  �����ŵĴ���
  ```cpp
  for(p1 = set, p2 = set+length-1; p1 < p2; p1++, p2--) {
    t = *p1;
    *p1 = *p2;
    *p2 = t;
  }
  ```

* ָ�����֮��ļӷ�������

* ָ���ά����Ԫ�ص�ָ��
  
  ��ά����Ԫ��a[i][j]�ı�ʾ
  ```cpp
  //��ʾ��ַ
  &a[i][j]
  a[i]+j
  *(a+i)+j
  
  //��ʾ��ֵ
  a[i][j]
  \*(a[i]+j)
  \*(\*(a+i)+j)
  (\*(a+i))[j]
  ```
  ע�⣺a[0] == a[0][0]

  һ��ͨ�õĶ�ά������������
  ```cpp
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
  ```

---

## <span id="2">2 ָ���뺯��</span>

### 2.1 �����Ĵ��ݷ�ʽ

* �������͵ı����������β�
  
  ��������x��y��ֵ�����û������͵ı����������β�
  ```cpp
  void swap(int a, int b) {
    int t;
    t = a;
    a = b;
    b = t;
  }
  ```
  ���ǵ����ֵ���ݣ��βεı仯����Ӱ��ʵ��

* ����������Ϊ�����β�

  ��������x��y��ֵ�����������������������β�
  ```cpp
  void swap(int& a, int& b) {
    int t;
    t = a;
    a = b;
    b = t;
  }
  ```
  ͨ�����屻�����еĲ���Ϊ�������ͣ�������������ֵ�ı�

* ָ��������Ϊ�����β�

  ��������x��y��ֵ������ָ�������������β�
  ```cpp
  void swap(int* px, int* py) {
    int t;
    t = *px;
    *px = *py;
    *py = t;
  }
  ```
  ͨ�����屻���ú����еĲ���Ϊָ�����ͣ�ͨ����Ӵ�ȡ������������ֵ�ı�

  ע�⣺ָ�������������βε���һ����ʽ������������������

### 2.2 ����ָ��ĺ�����ָ������ָ��

* ָ���ͺ���
  
  һ�������ķ���ֵ��ĳ���������͵ĵ�ֵַ����ָ���ͺ���
  ```cpp
  int* function(int x, int y) {
    return x+y;
  }
  ```

* ����ָ��
  
  ��������ڵ�ַ������ָ���������ָ������ڵ�ַ�ı�����
  ```cpp
  int (*fun)(int , int);
  int max(int x, int y) {
    return x > y?x : y;
  }
  fun = max;
  ```
  �÷�ʾ��
  ```cpp
  int process(int x, int y, int (*fun)(int, int)) {
    return fun(x, y);
  }
  ```

### 2.3 ָ��������ָ��ָ���ָ��

* ָ������
  
  һ�������������е�Ԫ�ض���ָ�������Ϊָ������

* ָ������������ָ��ı����������*��[]�����ȼ�˳��ͬ

  ```cpp
  int (*p)[M]; //p��һ������ָ�룬һ����ָ�룬ָ��ӵ��M��Ԫ�ص�һά����
  int* p[M]; //p��һ��ָ�����飬������M��ָ��
  ```

* main�����Ĳ���
  
  ��main()����ͷ�������ĸ�ʽΪ
  ```cpp
  int main(int argc, char* argv[])
  int main(int argc, char** argv)
  //argc��ʾ���������ַ����ĸ���
  //argv[]ָ���������еĸ����ַ���
  ```
  �ٸ����ӣ�ͨ�������в��������������ݵĺ�
  ```cpp
  int main(int argc, char* argv[]) {
    int sum, i;
    cout << "Command name:" << argv[0] << endl;
    for(sum = 0, i = 1; i < argc; i++) {
      sum += atoi(argv[i]);
    }
    cout << "Sum is:" << sum << endl;
  }
  ```

* ָ��ָ���ָ��
  
  �ٸ�����
  ```cpp
  int x, *p = &x, **pp = p;
  ```

### 2.4 �ڴ�Ķ�̬�������ͷ�

* �����洢�ռ�ķ�����ϵͳ��ɵģ������û���Ԥ
  
  * ��̬����������ʱ����ռ�
  
  * ��̬������ϵͳ�˶�ʱ����ռ�

* ����̬����ռ������û��ڱ��ʱ���ŵ�
* ������ٿռ�������ʱ���������һ��ͨ��ָ����ʿռ�
* new���ڶ�̬���봢��ռ䣬delete�����ͷ�new����Ĵ洢�ռ�
  ```cpp
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
  ```
  ע�⣺��������Ĳ�����һ��ָ�룬��Ҫ��ָ��ȥ���붯̬�ڴ棬�������Ϊ����Ŀռ��޷��ͷŶ�����ڴ�й©

### 2.5 void �� const ����ָ�����

#### 2.5.1 void����ָ�����

* void����ָ��
  
  void����ָ�������һ�ֲ�ȷ�����͵�ָ��

* �κ����͵�ָ�붼����ֱ�Ӹ���������������ת��

  ```cpp
  void* p1;
  int* p2;
  p1 = p2;
  ```

* ���ܶ�voidָ�������������

#### 2.5.2 const����ָ�����
  
* ָ������ָ��
  
  ���Ըı�ָ����ָ�Ŀռ䣬��������ͨ��ָ��ı�������ָ������

  ```cpp
  int i = 6;
  const int* p1 = &i;
  const int m = 16;
  *p1 = 16; //wrong
  p1 = &m; //true
  ```

* ����ָ��

  ���Ըı�ָ����ָ��ռ��е����ݣ����ǲ��ܸı�ָ���ָ��

  ```cpp
  char stringA[10] = "abcd", stringB[10] = "xyz";
  char* const sp = atringA;
  sp = stringB; //wrong
  *(sp+1) = 't'; //true
  ```

* ָ������ָ�볣��

  �Ȳ������޸�ָ����ָ�������ֲ��ɸı�ָ���ָ��

---

## <span id="3">3 �ṹ�����б�</span>

### 3.1 �ṹ��Ľ���

* �ṹ�����ͨ������һ���������ͣ��Ѳ�ͬ��������Ϊһ������������

* �ṹ����һ���ɳ���Ա�����ĳ�����������

* �ȶ���ṹ��
  ```cpp
  struct<�ṹ������> {
    <��Ա�б�>
  }; //���ﲻҪ������;��
  ```

* �ٶ������
  ```cpp
  student John, Mary;
  struct student John, Mary;
  ```

* Ҳ����ʹ���޽ṹ��������һ���Խṹ��
  ```cpp
  struct {
    int ID;
    char name[10];
  }John, Mary;
  ```

* ��ʼ���ṹ�����͵ı���

  ��{}��������ֵ�Խṹ��������г�ʼ��������
    ```cpp
    student John = {666, "Joe"};
    ```

  ��ͬ���͵Ľṹ�������ʼ������һ���ṹ�����
    ```cpp
    student Merry = John;
    ```

* �ṹ�����ͱ��������Ա������

  ���ýṹ������ĳ�Ա
  ```cpp
  John.ID = 2333;
  ```

  �������ýṹ�����
  ```cpp
  student John = {...};
  student Merry;
  Merry = John;
  ```

  ע��

  * ���ܽ��ṹ����Ϊһ�������������������

  * �ṹ������������������Ĳ��������ڰ�ֵ����

  * �������Է���һ���ṹ�����

### 3.2 �ṹ���Ӧ��

* ʹ�ýṹ�������Ϊ����������Ч�ʽϵͣ���Ϊ�ṹ����Ϊ�β���Ҫ��ֵ

* �ṹ��������ָ��

  ����ṹ������ͳ�ʼ��
  ```cpp
  student studentList[4];
  student studentList[4] = {{...}, {...}, {...}, {...}};
  ```

  ʹ�ýṹ������
  ```cpp
  //����Ԫ��
  for(int i = 0; i < 4; i++) {
    cout << studentList[i].name;
  }
  //ָ��
  student *ps;
  ps = stud;
  ps++;
  ```

### 3.3 typedef ����������

* �﷨��ʽ
  ```cpp
  tyoedef <ԭ������> <�Զ����������>
  ```

  ���ӣ�
  ```cpp
  typedef char NAME[100];
  NAME Joe;
  //�ȼ�������
  char Joe[100];
  ```

* ע��typedef��#define�Ĳ�ͬ

  * �ؼ���typedef�ڱ���׶���Ч���������ͼ��Ĺ���

  * #define�Ǻ궨�壬������Ԥ����׶Σ�ֻ����м򵥵��ַ��滻�������κμ��

  * #defineû������������ƣ�ֻҪ��֮ǰԤ������ĺ꣬���Ժ�ĳ����ж�����ʹ��

  * typedef������Լ���������

* ��typedef������������
  
  * typedefֻ������Ϊ��֪���������������µ�����������û�������µ���������

  * typedef���������ֲ
  
    ���綨��һ����REAL�ĸ������ͣ���Ŀ��ƽ̨һ�ϣ�������ʾ��߾��ȵ�����Ϊ
    ```cpp
    typedef long double REAL;
    ```

    ���ڲ�֧��long double�ĵڶ�ƽ̨�ϣ���Ϊ
    ```cpp
    typedef double REAL;
    ```

    ����double����֧�ֵ�ƽ̨�ϣ���Ϊ
    ```cpp
    typedef float REAL;
    ```

### 3.4 ����

* ���������

  * ���ݿռ���������
  
  * ʵ��Ӧ���޷�ȷ������Ĵ�С
  * �����㹻�󡪡������ռ��˷�

* ����Ľṹ
  ```cpp
  struct student {
    int ID;
    char name[20];
    student* next; //������ṹ�������
  };
  ```

* ��������
  
  ����ͷ�ڵ�ĵ�������

  ����ͷ�ڵ�ĵ�������

* �����Ӧ��ʾ��
  ```cpp
  #include "stdafx.h"
  #include <iostream>
  #include <iomanip>
  using namespace std;
  typedef struct node
  {
	  int data;
	  node *next;
  } NODE;
  NODE* initlist()
  {
      NODE *head;
      head = new NODE;
	  head->next = NULL;
	  return head;
  }
  
  NODE *create()
  {
	  NODE *p1, *p2, *head;
	  int a;
	  p2 = head = initlist();
	  cin >> a;
	  while ((a!=-1))
	  {
		  p1 = new NODE;
		  p1 -> data = a;
		  p2 -> next = p1;
		  p2 - p1;
		  cin >> a;
	  }
	  p2->next = NULL;
	  return(head);
  }
  void print(NODE* head)
  {
	  NODE *p;
	  p = head->next;
	  if (p != NULL)
	  {
		  cout << "Output list : ";
		  while (p != NULL)
		  {
			  cout << setw(5) << p->data;
			  p = p->next;
		  }
		  cout << "\n";
	  }
  }
  NODE* search(NODE* head, int x)
  {
	  NODE *p;
	  p = head->next;
	  while (p != NULL)
	  {
		  if (p->data == x)
			  return p;
		  p = p->next;
	  }
	  return NULL;
  }
  NODE *insert(NODE *head, NODE *s)
  {
	  NODE* p;
	  p = head;
	  while (p->next != NULL&&p->next->data < s->data)
		  p = p->next;
	  s->next = p->next;
	  p->next = s;
	  return head;
  }
  NODE *create_sort()
  {
	  NODE* p, *head = NULL;
	  int a;
	  head = initlist();
	  cin >> a;
	  while (a != 1)
	  {
		  p = new NODE;
		  p->data = a;
		  head = insert(head, p);
		  cin >> a;
	  }
	  return head;
  }
  NODE *delete_one_node(NODE *head, int num)
  {
	  NODE* p, *temp;
	  p = head;
	  while (p->next != NULL&&p->next ->data!=num)
		  p = p->next;
	  temp = p->next;
	  if (p->next != NULL)
	  {
		  p->next = temp->next;
		  delete temp;
	  }
	  else cout << "NOT found";
	  return head;
  }
  void free_list(NODE *head)
  {
	  NODE *p;
	  while (head)
	  {
		  p = head;
		  head = head->next;
		  delete p;
	  }
  }
  
  int main()
  {
	  //return 1;
	  NODE *st, *head = NULL;
	  int num; char c;
	  cout << "\n creat a list:\n";
	  head = initlist();
	  while (1)
	  {
		  cout << "\n\t D:Delete I:Insert P: Print S:Search E: Exit\n";
		  cin >> c;
		  switch (toupper(c))
		  {
		  case'I':
			  st = new NODE;
			  cout << "please input a number to be inserted:";
			  cin >> st->data;
			  insert(head, st);
			  break;
		  case 'D':
			  cout << "please input a number to be deleted:";
			  cin >> num;
			  delete_one_node(head, num);
			  break;
		  case 'S':
			  cout << "please input a number to be search:";
			  cin >> num;
			  if (search(head, num) != NULL)
			  {
				  cout << "it is in the list. \n";
			  }
			  else
				  cout << "It is not in the list. \n";
			  break;
		  case 'P':
		  	print(head);
			  break;
		  case 'E':
			  free_list(head);
			  exit(0);
		  default:
			  break;
		  }
	  }
	  return 0;
  }
  ```

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

* �����쳣

  �쳣���ڳ���ִ���ڼ��ͻ�����¼�

  �쳣�����ͬ���������ͨ������ϵͳ����

* �׳��쳣
  ```cpp
  float divide(int number, int div) {
    if(div == 0) {
      throw "ERROR: divided by zero";
    }
    else {
      return float(number) / div;
    }
  }
  ```

* �����쳣
  ```cpp
  try {
    <���ܳ����쳣�Ĵ���>
  }
  catch (exception param1) {
    <�����쳣����1�Ĵ���>
  }
  catch (exception param2) {
    <�����쳣����2�Ĵ���>
  }
  ```

* �쳣����ʧ�ܵ�ԭ��

  try���������Ͳ������쳣����catch���Բ����ָ��Ҫ��׽���쳣���Ͳ�ƥ��

  try���ķ�Χ̫С����try���֮ǰ���Ѿ��������쳣����ô�����try���齫����ִ��

* ���ڶ�����쳣����

  C++����֧�ֻ������͵��쳣�����⣬��֧�����������쳣����

  C++�ڴ���������͵��쳣ʱ��Ҫ����Щ�쳣����������ڲ�ͬ���ͣ����Ҷ���ÿ�����͵��쳣��Ҫ��дһ�ζ�Ӧ��catch����

  ���ӣ�
  ```cpp
  class IntRange {
    int input, lowest, highest;
  public:
    class tooLow {};
    class tooHigh {};
    InRange() {
      lowest = lowest;
      highest = highest;
    }
    int getInput() {
      cin >> input;
      if(input < lowest) {
        throw tooLow();
      }
      else if(input > highest) {
        throw tooHigh();
      }
      return input;
    }
  };
  int main() {
    InRange range;
    int uerValue;
    try {
      userValue = range.getInput();
    } 
    catch(IntRange::tooLow) {...}
    catch(IntRange::tooHigh) {...}
    return 0;
  }
  ```

  ������ͨ���쳣�����쳣��Ϣ���ݸ��쳣������
  ```cpp
  class IntRange2 {
    int input;
  public:
    class OutOfRange {
    public: 
      int value;
      OutOfRange(int i) {
        value = i;
      }     
    };
    int getInput() {
      cin>>input;
      if(...) {
        throw OutOfRange(input);
      }
      return iuput;
    }
  };
  int main() {
    IntRange2 range;
    int userValue;
    try {
      userValue = range.getInput();
    }
    catch (IntRange2::OutOfRange ex) {
      cout << ex.value;
    }
    return 0;
  }
  ```

* ע������
  
  * һ�������׳��쳣����ʹ���쳣�����Ժ󣬳���Ҳ���ܻص�ԭ�����׳������ִ��

  * һ�������׳��쳣��ִ��throw���ĺ���������ֹͣ����
  * ����ĺ�����Ա�׳����쳣����ô�������Ըö��������������
  * ��try���д����˶��󣬲�����Щ����δ���ü���������ô������Щ��������������������

* �ٴ��׳��쳣

  ```cpp
  try {
    ...
  }
  catch(exception param1) {
    ...
    throw; //����������ٴ��׳��쳣�����������������ϲ㺯������
  }
  catch(exception param2) {
    ...
  }
  ```


---

## <span id="9">9 ��׼ģ��STL</span>

### 9.1 STL ����

* ��׼ģ��⣺�������ݽṹ���㷨��ģ��ļ���

* �������������ɸ����������͵�ͨ�����ݽṹ������ģ��

* �������������������δ�ȡ�����е�Ԫ�أ�������ָ��

* �㷨���������������е�Ԫ�صĺ���ģ��

### 9.2 ����

* ˳������

  * vector

    ��̬���顣Ԫ�����ڴ�������ţ���������κ�Ԫ�ض����ڳ���ʱ�����
  
  * deque

    ˫����У�Ԫ������ѵ������ţ������ȡ�κ�Ԫ�ض����ڳ���ʱ����ɣ�����vector��
  
  * list

    ˫������Ԫ�����ڴ治��������ţ����κ�λ����ɾԪ�ض����ڳ���ʱ����ɣ���֧�������ȡ

* ��������

  * Ԫ��������ģ������κ�Ԫ�أ���Ӧ����Ӧ�����й�����ȷ��λ�ã���˾��нϺõ�����

  * ͨ����ƽ��������ķ�ʽʵ�֣������ڼ�����ʱ�䶼��O(log(N))

  * set/multiset
  
    set���Ǽ��ϣ�set�в�������ͬ��Ԫ�أ�multiset�������������ͬ��Ԫ��
  
  * map/multimap
  
    map��set�Ĳ�֮ͬ������map�д�ŵ�Ԫ�����ҽ�����������һ����first����һ����second�����Ҹ���first��ֵ����������ͼ�����multimap����������ͬ��firstԪ��

* ����������

  * stack

    ջ��������������У��������������б�ɾ�����������޸ĵ���ֻ������������е������ȳ�
  
  * queue

    ���У�����ֻ������β�����У�ɾ�����������޸�ֻ�����ͷ�����У��Ƚ��ȳ�
  
  * priority_queue

    ���ȶ��У�������ȼ�Ԫ�����ǵ�һ������

* ˳�������͹��������н��еĺ�����Ա
  
  |������|����|
  |:-:|:-|
  |begin|����ָ�������е�һ��Ԫ�صĵ�����|
  |end|����ָ�����������һ��Ԫ�غ���λ�õĵ�����|
  |rbegin|����ָ�����������һ��Ԫ�صĵ�����|
  |rend|����ָ�������е�һ��Ԫ��ǰ���λ�õĵ�����|
  |erase|��������ɾ��һ�����߼���Ԫ��|
  |clear|��������ɾ������Ԫ��|

* ˳�������ĳ��ó�Ա����

  |������|����|
  |:-:|:-|
  |front|���������е�һ��Ԫ�ص�����|
  |back|�������������һ��Ԫ�ص�����|
  |push_back|������ĩβ�����µ�Ԫ��|
  |pop_back|ɾ������ĩβ��Ԫ��|
  |erase|ɾ��������ָ���Ԫ�أ����ܻ�ʹ��ʧЧ��������ɾ��һ�����䣬���ر�ɾ��Ԫ�غ����Ԫ�صĵ�����|

### 9.3 ������

* ����ָ��˳�������͹��������е�Ԫ�أ��÷���ָ������

* ��const�ͷ�const���֣�ͨ����const�����޸���ָ���Ԫ��

* ͨ����������Զ�ȡ��ָ���Ԫ��

* ������ʾ��
  ```cpp
  int main() {
    vector<int> v;
    v.push_back(1);

    vector<int>::const_iterator i;
    for(i = v.begin(); i != v.end(); ++i) {
      cout<<*i<<",";
    }
    cout<<endl;
    return 0;
  }
  ```

* ˫�������

  ��p��p1����˫�����������ɶ�p��p1�������²���

  |||
  |:-:|:-|
  |++p, p++|ʹpָ�������е���һ��Ԫ��|
  |--p, p--|ʹpָ�������е���һ��Ԫ��|
  |*p|ȡpָ���Ԫ��|
  |p = p1|��ֵ|
  |p == p1, p != p1|�ж��Ƿ���ȡ�����|

* ������ʵ�����

  ��p��p1����������ʵ���������ɶ�p��p1�������²���

  |||
  |:-:|:-|
  |p += i|��p����ƶ�i��Ԫ��|
  |p -= i|��p��ǰ�ƶ�i��Ԫ��|
  |p + i|ָ��p����ĵ�i��Ԫ�صĵ�����|
  |p - i|ָ��pǰ��ĵ�i��Ԫ�صĵ�����|
  |p[i]|p�����i��Ԫ�ص�����|
  |p < p1, p <= p1...|�Ƚϴ�С|
  |p - p1|����p��p1֮���Ԫ�ظ���|

* С�ܽ�
  |����|�����ϵĵ��������|
  |:-:|:-:|
  |vector|�������|
  |deque|�������|
  |list|˫�����|
  |set/multiset|˫�����|
  |map/multimap|˫�����|
  |stack|��֧�ֵ�����|
  |queue|��֧�ֵ�����|
  |priority_queue|��֧�ֵ�����|

  ע��

  * �е��㷨����sort��binary_search��Ҫͨ��������ʵ����������������е�Ԫ��

  * ˫���������֧�� < ��list����Ҳû�� [ ] ��Ա����

  * ������ʵ���������ͨ�� v[i] �����ʳ�Ա

### 9.4 �㷨


















  