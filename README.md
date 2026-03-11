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

// 1 
