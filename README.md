# ATM-INTERFACE
package basic_javaGB1108;
import java.util.*;
import java.text.*;
 class Account
{
	Scanner input=new Scanner(System.in);
	DecimalFormat df=new DecimalFormat("'Rupee '###,##0.00");
	int CN;
	int PN;
	double CB=2000;
	double SB=1000;
	void setCustomerNumber(int cn)
	{
		CN=cn;
		//system.out.println(CN);
	}
	void setPinNumber(int pn)
	{
		PN=pn;
		//system.out.println(PN);
	}
	int getCustomerNumber()
	{
		return CN;
	}
	int getPinNumber()
	{
		return PN;
	}
	 void getCurrentBalance() 
	 {
		System.out.println("Your Current Account Balance : "+df.format(CB));
	}
	 void getSavingBalance() 
	 {
		System.out.println("Your Current Account Balance : "+df.format(SB));
	}
	  void inputCurrentWIthdraw()
	 {
		 System.out.println("Your Current Account Balance : "+df.format(CB));
		 System.out.println("Enter Amount You Want to Withdraw From Your Current Account :");
		 double amount=input.nextDouble();
		 if((CB-amount)>=0) 
		 {
			 outputCurrentWIthdraw(amount);
			 System.out.println("Your Current Account Balance : "+df.format(CB));
		 }
		 else
		 {
			 System.out.println("Insufficient Balance");
		 }
	 }
	 double outputCurrentWIthdraw(double amount)
	  {
		  CB=CB-amount;
		  return CB;
	  }
	 double outputSavingWithdraw(double amount)
	 {
		 SB=SB-amount;
		 return SB;
	 }
	 void inputSavingWithdraw()
		{
			System.out.println("Your Current Account Blanace :  "+df.format(SB));
			System.out.println("Amount You Want to Withdraw From Your Saving Account");
			double amount = input.nextDouble();
			if((SB - amount)>= 0)
			{
				outputSavingWithdraw(amount);
				System.out.println("Your Current Account balance : "+df.format(SB));
			}
			else
			{
				System.out.println("Insufficient Balance ");
			}
		}
		void inputCurrentDeposit()
		{
			System.out.println("\nYour Current Account Blanace :  "+df.format(CB));
			System.out.println("\nEnter Amount You Want to Deposit to Your Current Account");
			double amount = input.nextDouble();
			if((CB + amount)>= 0)
			{
				outputCurrentDeposit(amount);
				System.out.println("\nYour Current Account balance : "+df.format(CB));
			}
			else
			{
				System.out.println("\nInsufficient Balance ");
			}
		}
		double outputCurrentDeposit(double amount)
		{
			CB = CB + amount;
			return CB;
		}
		void inputSavingDeposit()
		{
			System.out.println("\nYour Current Account Blanace :  "+df.format(SB));
			System.out.println("\nEnter Amount You Want to Deposit To Your Saving Account");
			double amount = input.nextDouble();
			if((SB + amount)>= 0)
			{
				outputSavingDeposit(amount);
				System.out.println("\nYour Current Account balance : "+df.format(SB));
			}
			else
			{
				System.out.println("\nInsufficient Balance ");
			}
		}
		double outputSavingDeposit(double amount)
		{
			SB = SB + amount;
			return SB;
		}
}
class Option_menu_1108 extends Account
{
	Scanner input = new Scanner(System.in);
	HashMap<Integer, Integer> data = new HashMap<Integer, Integer>();
	
	void getLogin()
	{
		int i=125;
		do 
		{
			try
			{
				data.put(11111, 111);
				data.put(11112, 222);
				data.put(11113, 333);
				data.put(11114, 444);
				data.put(11115, 444);
				
				System.out.println("Welcome to the VKP ATM");
				System.out.println("Enter your customer number");
				setCustomerNumber(input.nextInt());
				
				System.out.println("Enter your pin number");
				setPinNumber(input.nextInt());
			    int A = getCustomerNumber();
				int B = getPinNumber();							
				
				if(data.containsKey(A) && data.get(A) == B)
				{
					getAccountType();
				}
				else
				{
					System.out.println("Login unsuccessful");
				}
			}
			catch(InputMismatchException h)
			{
				System.out.println("please enter only numbers");
				System.out.println("Charactors and symbols are not allowed");
				i=450;
			}	
		}while(i==125);
	}
	void getAccountType()
	{
		System.out.println("Select the account type you want to access");
		System.out.println("Type1:Current Account");
		System.out.println("Type2:Saving Account");
		System.out.println("Type3:Exit");
		System.out.println("Choice:");
		int choice=input.nextInt();
		switch(choice)
		{
		case 1 :getCurrent();
			break;
		case 2 :getSaving();
			break;
		case 3 :
			System.out.println("Thank you for using this ATM, VISIT AGAIN");
			break;
		default :
			System.out.println("Invalid choice");
			System.out.println("Please Enter Vaild choice");
			break;
		}
	}
	void getCurrent()
	{
		System.out.println("Current Account");
		System.out.println("Type 1 : View Balance");
		System.out.println("Type 2 : Withdraw fund");
		System.out.println("Type 3 : Deposite Fund");
		System.out.println("Type 4 : Exit");
		System.out.println("Choice :");	
		
		int Choice=input.nextInt();
		switch(Choice)
		{
		case 1 :
			getCurrentBalance();
			getCurrent();
			break;
		case 2 :
			inputCurrentWIthdraw();
			getAccountType();
			break;
		case 3 :
			break;
		case 4 :
			System.out.println("Thank you for using this ATM, VISIT AGAIN");
			break;
		default :
			System.out.println("Invalid choice");
		    System.out.println("Please Enter Vaild choice");
			break;
		}
	}
	void getSaving()
	{
		System.out.println("Saving Account");
		System.out.println("Type 1 : View Balance");
		System.out.println("Type 2 : Withdraw fund");
		System.out.println("Type 3 : Deposite Fund");
		System.out.println("Type 4 : Exit");
		System.out.println("Choice :");	
		
		int Choice=input.nextInt();
		switch(Choice)
		{
		case 1 :
			getSavingBalance();
			getSaving();
			break;
		case 2 :
			inputSavingWithdraw();
			getAccountType();
			break;
		case 3 :
			break;
		case 4 :
			System.out.println("Thank you for using this ATM, VISIT AGAIN");
			break;
		default :
			System.out.println("Invalid choice");
		    System.out.println("Please Enter Vaild choice");
			break;
		}
	}
}
public class ATM_VKP
{
		public static void main(String[] args)
		{
			Option_menu_1108 op = new Option_menu_1108();
			op.getLogin();
		}
}







