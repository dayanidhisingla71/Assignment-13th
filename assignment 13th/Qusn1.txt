class Thread1 extends Thread
{
	int i=1;
	public synchronized void run()
	{
		while(i<500) 
		{
			System.out.println(i);
			i++;
		}
		try 
		{
			Thread.sleep(100);
		}
		catch(InterruptedException e) 
		{
			e.printStackTrace();
		}
	}
}
class Thread2 implements Runnable
{
	int i=500;
	public synchronized void run() 
	{
		while(i<=1000)
		{
				System.out.println(i);
				i++;
		}
		try 
		{
			Thread.sleep(100);	
		}
		catch(InterruptedException e)
		{
			e.printStackTrace();
		}
	}
	
	public static void main(String[] args) throws InterruptedException 
	{
		Thread1 t = new Thread1();
		Thread t1 = new Thread(t);
		t1.start();
		Thread2 th2 = new Thread2();
		Thread t2 = new Thread(th2);
		t1.join();
		t2.start();
		t2.join();

	}
	
}