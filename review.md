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
  string name("LiSA");
  string singer(name);
  
  </pre>
---

## <span id="2">2 ָ���뺯��</span>

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

