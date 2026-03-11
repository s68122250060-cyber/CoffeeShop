# Phase 1: หลายออเดอร์ท าพร้อมกัน
คำถามอภิปราย (อธิบาย)

public class CoffeeShop {
  public static void main(String[] args) {

    Thread t1 = new Thread(new CoffeeMaker("Espresso"));
    Thread t2 = new Thread(new CoffeeMaker("Latte"));
    Thread t3 = new Thread(new CoffeeMaker("Cappuccino"));

    t1.start();
    t2.start();
    t3.start();

    System.out.println("🛎 รับออเดอร์ครบแล้ว");
  }
}

## 1 ตอบ เพราะว่า Thread ทำงานพร้อมกัน (Concurrency) และถูกจัดการโดย Thread Scheduler ของ JVM / OS

public class CoffeeShop {
  public static void main(String[] args) {

    Thread t1 = new Thread(new CoffeeMaker("Espresso"));
    Thread t2 = new Thread(new CoffeeMaker("Latte"));
    Thread t3 = new Thread(new CoffeeMaker("Cappuccino"));

    t1.run();
    t2.run();
    t3.run();
        System.out.println("🛎 รับออเดอร์ครบแล้ว");
  }
}

## 2 ตอบ ไม่เกิด Multi – Thread เพราะ run เป็น Method ธรรมดา 

## 3 main thread ทำงานพร้อมกับ CoffeeMaker หรือไม่?
ตอบ ทำงานพร้อมกัน

# Phase 2: ปัญหาเครื่องชงมีเครื่องเดียว (Race Condition)
ร้านมี “เครื่องชงกาแฟแค่ 1 เครื่อง” แต่หลาย thread พยายามใช้พร้อมกัน


