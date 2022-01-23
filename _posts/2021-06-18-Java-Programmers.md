---
title: 9.Java-Programmers lv1 
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


### 1. 직사각형 별찍기 


``` java


public class lv1 {

    @RequiresApi(api = Build.VERSION_CODES.N)
    public static void main2(String[] args){
        Scanner sc = new Scanner(System.in);
        int a = sc.nextInt();
        int b = sc.nextInt();

//        for(int i = 0 ; i < b; i++){
//            for (int j = 0 ; j < a; j++){
//                System.out.print("*"); // 연속 찍기
//            }
//            System.out.println();
//        }

        StringBuilder sb = new StringBuilder();

        IntStream.range(0,a).forEach(s -> sb.append("*"));
        IntStream.range(0,b).forEach(s -> System.out.println(sb));


    }
}




```

<br/>
<br/>


### 2. 평균 구하기 

``` java



public class lv12 {

    @RequiresApi(api = Build.VERSION_CODES.N)
    public double solution(int[] arr) {
//        double answer = 0;
//        for(int i = 0; i < arr.length; i ++ ){
//            answer += arr[i];
//        }
//
//        return answer/(double)arr.length;

        return Arrays.stream(arr).average().getAsDouble();

    }

    @RequiresApi(api = Build.VERSION_CODES.N)
    public static void main(String[] args){
        int x[] = {1,2,3,4};
        lv12 sol = new lv12();
        System.out.println(sol.solution(x));
    }

}


```

<br/>
<br/>


### 3. 두 정수 사이의 합 

``` java


public class lv13 {

    public long solution(int a, int b) {
        long answer = 0;
        int max = Math.max(a, b);
        int min = Math.min(a, b);
        for(int i = min ; i<=max; i++) {
            answer += i;
        }
        return answer;
    }

    public static void main2(String[] args){
        lv13 sum = new lv13();

        System.out.println(sum.solution(1,5));

    }

}


```


<br/>
<br/>


### 4.  2016년 

``` java 


public class lv14 {


    public static String solution(int a, int b) {
//        int total = 0;
//        String w[] = {"FRI", "SAT", "SUN", "MON", "TUE", "WED", "THU"};
//        int m[] = {31, 29, 31, 30, 31, 30,31, 31, 30, 31, 30, 31};
//        for(int i =0;i<a-1;i++){
//            total += m[i];
//        }
//        total += b-1;
//        String answer = w[total%7];
//        return answer;

        String answer = "";
        Calendar cal = Calendar.getInstance(); // 추상클래스기 때문에 싱글톤 방식으로 객체생성

        // new()와 getInstance()의 차이
       //new()          : 객체를 계속계속 만들 수 있다.
        //getInstance()  : 싱글턴패턴, 하나의 인스턴스만 가지고 공유해서 쓴다.

        cal.set(2016,a-1,b); // 캘린더의 필드에 따른 파라미터 설정
        Date date = cal.getTime(); // 객체를 Data 객체로 변환
        SimpleDateFormat sdf = new SimpleDateFormat("E", Locale.ENGLISH);

        answer = sdf.format(date).toUpperCase();

        return answer;
    }


    public static void main(String[] args){
        lv14 tt = new lv14();
        System.out.println(lv14.solution(2,3));
    }


}



```



<br/>
<br/>


### 5. 짝수와 홀수 

``` java


public class lv15 {

    public static String solution(int num){
//        if (num % 2 == 0 ){
//            return ("Even");
//        } else {
//            return "Odd";
//        }
        return num % 2 == 0 ? "Even" : "Odd";

        
    }

    public static void main(String[] args){
        System.out.println(lv15.solution(3));
    }


}

```


<br/>
<br/>


### 6. x만큼 간격이 있는 n개의 수

``` java


public class lv16 {

    public static long[] solution(int x, int n) {
        long[] answer = new long[n];
        long temp = x;

        for (int i = 0; i < n; i++) {
            answer[i] = temp * (i + 1);
        }

        return answer;
    }


        public static void main2(String[] args) {
            lv16 aa = new lv16();


            System.out.println(Arrays.toString(aa.solution(2, 5)));

        }


}

```



<br/>
<br/>


### 7. 핸드폰 번호 가리기 

``` java



public class lv17 {

    public String solution(String phone_number) {
        String answer = "";
        for(int i=0; i < phone_number.length();i++){
            if (i<phone_number.length()-4){
                answer += "*";
            } else {
                answer += phone_number.charAt(i);
            }
        }
        return answer;
    }

    public static void main(String[] args){
        lv17 aa = new lv17();
        System.out.println(aa.solution("01091455555"));
    }

}




```




<br/>
<br/>




### 8. 제일 작은 수 제거하기 

``` java


public class lv18 {
    public static int[] solution(int[] arr) {
        int min = arr[0];
        int[] answer = new int[arr.length - 1];
        if (arr.length <= 1) {
            int[] answer2 = { -1 };
            return answer2;
        } // 빈배열 리턴
        for (int i = 0; i < arr.length; i++) {
            if (min > arr[i]) {
                min = arr[i];
            }
        } // 가장 작은수 비교 , 교체

        int index = 0;
        for (int j = 0; j < arr.length; j++) {
            if (min == arr[j]) {
                continue; // 배열이 최소값이라면 리스트에 담지않고 pass
            } else {
                answer[index++] = arr[j]; // index0에 arr[0]을 추가 후 ++로 다음 index1를 1로
            }
        }
        return answer;
    }

    public static void main(String[] args) {
        int[] arr = {4, 3, 2, 1};
        System.out.println(Arrays.toString(solution(arr)));

    }
}
