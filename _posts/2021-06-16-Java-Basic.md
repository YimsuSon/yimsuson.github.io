---
title: 7.Java-Basic2
excerpt: Android


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
  - Android

tags:
  - Android
  - "2021"
  - "2021.06"



---

1.Java -  basic

<br/>

### 1. Array , List , Generics , Switch , While, for , for-each 

<br/>
<br/>

``` java


public class a_array {
    public static int count;

    public static void main(String[] args){

        /*
        // Array
        int[] odds = {1,3,5,6};
        String[] weeks = {"a","b","c"};

        weeks[0] = "월"; // 값 교체

        for (int i = 0; i < weeks.length ;i++){
            System.out.println(weeks[i]);
        }

         */



        /*

        // List - add, size, contains, remove

        ArrayList pitches = new ArrayList();
        pitches.add("133");
        pitches.add("222");
        pitches.add("333");


        pitches.add(2,"444"); // 3번째 인덱스에 추가


        // System.out.println(pitches.size()); // 갯수 리턴

        // System.out.println(pitches.contains("222")); // 포함하면 true

        // System.out.println(pitches.remove("133")); // 항목제거 후 true

        // System.out.println(pitches.remove(0));
        */


        /*
        // Generics
        ArrayList ListA = new ArrayList();
        ListA.add("hi");
        ListA.add("java");

        String hi = (String) ListA.get(0); // Object를 String 으로 캐스팅 필요
        String java = (String) ListA.get(1);

        ArrayList<String> ListB = new ArrayList<>(String)();
        ListB.add("hi");
        ListB.add("java");

        String hii = ListB.get(0); // 형번환중 오류 발생이 줄어든다
        */


        /*
        // Map - put, get, containsKey, remove, size ( Dictionary )
        // Map 에는 HashMap, LinkedHashMap, TreeMap 등이 있다
        HashMap<String,String> map = new HashMap<String,String>() ;
        map.put("people","사람");
        map.put("baseball","야구");

        // System.out.println(map.get("people")); // key를 사용해서 value를 가져온다
        // System.out.println(map.containsKey("people")); // 존재하면 true
        // System.out.println(map.remove("people")); // 삭제 후 삭제한값 return
        System.out.println(map.size()); // Map 안의 갯수

         */


        /*

        // if - contains , else if

//        boolean money = true;
//        if (money) {
//            System.out.println("a");
//        } else {
//            System.out.println("b");
//        }

//        int money = 2000;
//        boolean harCard = true;
//
//        if (money > 3000 || harCard) {
//            System.out.println("aa");
//        } else {
//            System.out.println("bb");
//        }

        ArrayList<String> pocket = new ArrayList<>();
        pocket.add("paper");
        pocket.add("head");
        pocket.add("money");
        if (pocket.contains("money")){
            System.out.println("aa");
        } else {
            System.out.println("bb");
        }

        boolean hasCard = true;
        if (pocket.contains("money")) {
            System.out.println("aa");
        } else if (hasCard) {
            System.out.println("bb");
        } else {
            System.out.println("cc");
        }

        */


        /*
        // switch/case
        int month = 2;
        String monthString = "";
        switch (month){
            case 1: monthString = "Jan";
                break;
            case 2: monthString = "Feb";
                break;
            case 3: monthString = "Mar";
                break;
            default: monthString ="invalid";
                break;
        }
        System.out.println(monthString);
        */

        /*
        // while
        int treeHit = 0;
        while (treeHit < 5){
            treeHit++;
            System.out.println("나무를 "+ treeHit + "번 찍었습니다 ");
            if (treeHit == 3){
                System.out.println("나무가 넘어감 ");
                break;
            }
        }

        int a = 0 ;
        while (a < 10) {
            a++;
            if(a % 2 == 0 ){
                continue;
            }
            System.out.println(a);
        }
        */


        /*
        // for
        int[] marks = {90,25,67,45,80};
        for (int i = 0; i <marks.length; i++ ) {
            if (marks[i] < 60 ) {
                continue;
            }
            System.out.println( (i+1) + "번 학생 축하");
        }


        */

        /*
        // for each
        ArrayList<String> numbers = new ArrayList<String>();
        numbers.add("one");
        numbers.add("two");
        numbers.add("three");

        for (String num : numbers){ // ( 타입 객체명 : 객체 )
            System.out.println(num);
        }
        */

        /*
        // class
        a_animal cat = new a_animal(); // 객채 생성
        cat.setName("baby"); // 메소드 호출
        System.out.println(cat.name); // a_animal 클래스에 있는 객체 변수를 가져온다

        cat.setType("much");
        System.out.println(cat.name);

        a_animal dog = new a_animal();
        dog.setType("phome");
        System.out.println(dog.name); // 객체 변수는 공유되지 않기 때문에 각각 출력된다

        */


        // method
        // 평범함 메소드
         a_animal myTest = new a_animal();
        int c = myTest.sum(1,2);
        System.out.println(c);
        // 입력 값이 없는 메소드
        a_array myTest2 = new a_array();
        String cc = myTest2.sqy();
        System.out.println(cc);
        // return 값이 없는 메소드
        a_array myTest3 = new a_array();
        myTest3.sum2(3,4);


        // call by value - 값 변경 x
        a_array myCounter = new a_array();
        System.out.println("befre :" + myCounter.count);
        a_animal myUpdater = new a_animal();
        myUpdater.update(myCounter); // update 메소드가 객체를 받으면 call-by-reference가 된다
        System.out.println("after :" + myCounter.count);

        // myUpdater.update(myCounter.count); // 메소드가 int값을 받으면 call-by-value가 된다



        // 생성자 constructor - 객체 생성시 객체변수값 생성 강제
        // 인터페이스 interface - 다중상속지원 (class는 단일상속 )
        // 다형성 polymorphism - 하나의 객체가 여러개의 자료형 타입을 가지는것
        // 추상클래스 Abstract class -

    }


    // method
    // 평범함 메소드
    public int sum(int a, int b) {
        return a+b;
    }

    // 입력 값이 없는 메소드
    public String sqy(){
        return "Hi";
    }

    // return 값이 없는 메소드
    public void sum2(int a, int b ){
        System.out.println(a + "와" + b + "의 합은 " + (a+b)+ "입니다 ");
    }

    // return 의 또 다른 쓰임새
    public void say_nick(String nick){
        if ("fool".equals(nick)){
            return; //  "fool" 이 들어오면 빠져나간다
        }
        System.out.println("나의 별명은 "+ nick + "입니다 ");
    }




}





```


<br/>
<br/>
 


