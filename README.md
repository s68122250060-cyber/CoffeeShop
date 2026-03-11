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

## 1 ตอบ จะทำงานพร้อมกัน แต่ชื่อจะโผล่มาทีละตัว ไปจนครบ สลับกันโผล

## 2 ตอบเมนูที่ออกมาจะเสร็จไม่เท่ากัน จะช้ากว่าหรือเร็วกว่า ขึ้นอยู่ที่ เวลาที่สุ่ม 2 กับ 3 วิ

## 3 ตอบ ไม่เกิด Multi – Thread เพราะ run เป็น Method ธรรมดา

## 4 ตอบ เมื่อเพิ่มคำสั่งนี้ อาจพบว่า ข้อความ End main แสดงก่อนที่การชงกาแฟจะเสร็จ เพราะ main thread ทำงานเสร็จเร็วกว่า ในขณะที่ Thread อื่นยังทำงานอยู่

## 5 ตอบ การใช้synchronized จะช่วยให้ Thread เข้าใช้งานเครื่องชงกาแฟได้ทีละตัว ป้องกันปัญหา Race Condition ส่วน AtomicInteger ใช้ส าหรับจัดการตัวนับ เช่น หมายเลขออเดอร์ ให้ปลอดภัยเมื่อหลาย Thread ใช้งานพร้อมกัน
