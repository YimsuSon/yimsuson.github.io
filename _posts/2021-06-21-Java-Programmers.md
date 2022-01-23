---
title: 10.Java-Programmers lv1 
excerpt: Algorithm


#최상위 사진
header:
  #image: /assets/images/moon3.png
  teaser: /assets/images/moon3-th.png

gallery:
  - url: /assets/images/unsplash-gallery-image-1.jpg
    image_path: assets/images/unsplash-gallery-image-1-th.jpg
    alt: "placeholder image 1"
  - url: /assets/images/unsplash-gallery-image-2.jpg
    image_path: assets/images/unsplash-gallery-image-2-th.jpg
    alt: "placeholder image 2"
  - url: /assets/images/unsplash-gallery-image-3.jpg
    image_path: assets/images/unsplash-gallery-image-3-th.jpg
    alt: "placeholder image 3"
    


 #사이드바 설정 
sidebar:
  - title: "Role"
    nav: sidebar-sample

# 해당 글 목차
toc: true
toc_sticky: true

toc_label: "Yimsu's Blog"
toc_icon: "cog"


## 테그설정

categories:
  - Algorithm

tags:
  - Algorithm
  - "2021"
  - "2021.06"



---




- call-by reference. 메소드.int.값변화x
- 생성자. 리턴없는메소드 . 필드값 초기화
- interface .다중상속 .생성자x
- 다형성 - 객체1개가 여러타입
- abstract. 메소드,필드강제  - 생성자o 
- 오버로딩 - new 메소드 생성
- 오버라이딩 - 상속 메소드 내용 변경
- enum - 클래스같은 상수. 
- 람다 - first class citizen (전저리)
- 스트림 - 배열(collection) 탐색도구
- implement 인터페이스  , extend 상속 






10 Java-programmers lv1

<br/>
<br/>

### 9. 정수 내림차순으로 배치

<br/>
https://programmers.co.kr/learn/courses/30/lessons/12933?language=java

<br/>

``` java


public int reverseInt(int n){

    String str = Integer.toString(n);
    char[] c = str.toCharArray();
    Arrays.sort(c); // 프로그래머스에 문제있음 // 오름차순정렬


    StringBuilder sb = new StringBuilder(new String(c,0,c.length));

    return Integer.parseInt((  (sb.reverse()).toString() ) ); // 내림차순정렬
}

// 아래는 테스트로 출력해 보기 위한 코드입니다.
public static void  main(String[] args){
    lv19 ri = new lv19();
    System.out.println(ri.reverseInt(118372));
}



```

<br/>
<br/>

### 10. 자연수 뒤집어 배열로 만들기 


<br/>
https://programmers.co.kr/learn/courses/30/lessons/12932?language=java
<br/>

``` java



public class lv110 {

    public static int[] solution(long n) {
        String a = "" + n;
        int[] answer = new int[a.length()];
        int cnt = 0;

        while (n>0){
            answer[cnt] = (int)(n%10); // n%10을 int로 캐스팅
            n /= 10; // 기존값에 우측항을 나눔
            cnt++;
        }
        return answer;
    }
    public static void main(String[] args) {
        lv110 dd = new lv110();
        System.out.println(Arrays.toString(solution(12345)));
    }

}




```

<br/>
<br/>

### 11. 행렬의 덧셈 


<br/>
https://programmers.co.kr/learn/courses/30/lessons/12950
<br/>


``` java


public class lv111 {
    public int[][] solution(int[][] arr1, int[][] arr2){

        int col = Math.max(arr1.length,arr2.length);
        int row = Math.max(arr1[0].length , arr2[0].length);
       
        int [][] answer = new int[col][row];

        for (int i = 0; i < answer.length ; i++){
            for(int j = 0; j < answer[i].length ; j++){
                answer[i][j] = arr1[i][j] + arr2[i][j];
            }
        }

        return answer;
    }

    public static void main(String[] args){
        lv111 dd = new lv111();
        int[][] arr1 = new int[][] { {1,2},{2,3}};
        int[][] arr2 = new int[][] { {3,4},{5,6}};
        int[][] result = dd.solution(arr1,arr2);
        if (result[0][0] == 4) {
            System.out.println("정답");
        }

    }
}



```

<br/>
<br/>

### 12. 소수 찾기 

<br/>
https://programmers.co.kr/learn/courses/30/lessons/12921
<br/>

``` java


public class lv112 {

    public int solution(int n) {
        int answer = 0;
        for(int i = 2; i <= n; i++){
            int j = 2;
            int cnt = 0;

            while(j <= (int)Math.sqrt(i)){
                if(i % j == 0){
                    cnt += 1;
                    break;
                }
                j += 1;
            }
            if(cnt == 0) answer += 1;
        }
        return answer;
    }

    public static void main(String[] args) {
        lv112 prime = new lv112();
        System.out.println( prime.solution(10) );
    }


}


```

<br/>
<br/>

### 13. 시저 암호 


<br/>
https://programmers.co.kr/learn/courses/30/lessons/12926?language=java
<br/>

``` java


public class lv113 {

       public String solution(String s, int n) {
            String answer = "";
            n = n % 26;


            for (int i = 0; i < s.length(); i++) {
                char ch = s.charAt(i);  // i번째 문자열을 ch 에 넣는다

                if (Character.isLowerCase(ch)) {
                    ch = (char) ((ch - 'a' + n) % 26 + 'a');
                } else if (Character.isUpperCase(ch)) {
                    ch = (char) ((ch - 'A' + n) % 26 + 'A');
                }
                answer += ch;
            }
            return answer;
        }

        public static void main(String[] args) {
            lv113 c = new lv113();
            System.out.println("s는 'a B z', n은 4인 경우: " + c.solution("c B z", 4));



            char a1 = 'a'; // 97 Dec
            char a2 = a1; // char 'a'
            int i = a2 + 1 ; // int 98 , a2 자동 변환
            char a3 = (char)(a1 + 2); // 99 를 char로 변환
            a2 ++;

            System.out.println(i + "\t" + a2+ "\t" + a3); // char 타입은 정수형이기 때문에 더하기 빼기 가능

            char a11 = 'a'; // char '' string ""
            // char a22 = a11 + 1; 변수 + 리터럴이기 때문에  컴파일 에러
            char a33 = 'a' + 1 ; // 문자리터럴 + 정수리터럴이기 때문에 가능
            


            System.out.println(a33);

       }
}



```


<br/>
<br/>









<br/>


![image](/assets/images/asciiTable.png)

<br/>


