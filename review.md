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

