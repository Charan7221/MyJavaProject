# MyJavaProject
package Package_Project;
import java.time.LocalDate;
import java.util.Random;
import java.util.Scanner;
abstract class Project
{
	static Scanner sc = new Scanner(System.in);
	private String email ;
	private String password ;
	private String mobile_number;
	int cvv;
	boolean isMobileNumberValid(String mobile_number) 
	{
		return mobile_number.length() == 10 && (mobile_number.startsWith("9") || 
						mobile_number.startsWith("8") || 
	        				mobile_number.startsWith("7") || 
	            				mobile_number.startsWith("6"));
	}
	public void register() 
	{
        	System.out.println("=======================================");
        	System.out.println("        WELCOME TO REGISTRATION        ");
        	System.out.println("=======================================");
    		while (true) 
    		{
        		System.out.print("Enter mobile number for registration: ");
        		mobile_number = sc.next();
        		if(isMobileNumberValid(mobile_number))
        		{
            			break;
        		} 
        		else 
        		{
            			System.out.println("Invalid phone number, please try again.");
        		}
    		}	

        	int otp = 0;
        	int random;
        	int min = 1000;
        	int max = 9999;
        	int op = 0;
        	Random rand = new Random();
        	random = rand.nextInt(max - min + 1) + min;
        	System.out.println("Generated random number: " + random);

    		while (op < 3) 
    		{
        		System.out.print("Enter OTP: ");
        		otp = sc.nextInt();
        		if (random == otp) 
        		{
            			break;
        		} 
        		else 
        		{
            			if (op == 2) 
            			{
                			System.out.println("You have made too many attempts.");
            			}
            			System.out.println("Invalid OTP, please try again.");
            			op++;
        		}
    		}
    		if (random != otp) 
    		{
        		System.out.println("OTP validation failed. Please try registering again.");
        		register();
        		return; 
    		}
	
    		while (true) 
    		{	
        		System.out.println("Enter your Email for Registration:");
        		email = sc.next();
        		if (email.toLowerCase().endsWith("@gmail.com"))
        		{
            			break;
        		} 
        		else
        		{
            			System.out.println("Invalid email! Email should be in this format: your.email@gmail.com");
        		}
    		}

    		while (true) 
    		{
        		System.out.println("Enter your Password:");
        		password = sc.next();
        		int special = 0;
        		int digit = 0;
        		int lower = 0;
        		int upper = 0;

        		if (password.length() >= 8) 
        		{
            			for (int i = 0; i < password.length(); i++) 
            			{
                			char chh = password.charAt(i);
                			if (chh >= 'a' && chh <= 'z') 
                			{
                    				lower++;
                			} 
                			else if (chh >= 'A' && chh <= 'Z')
                			{
                    				upper++;
                			}
                			else if (chh >= '0' && chh <= '9')
                			{
                    				digit++;
                			} 
                			else if ("[]!@#$%^&*".indexOf(chh) >= 0)
                			{
                    				special++;
                			}
            			}

            		if (special >= 1 && digit >= 1 && lower >= 1 && upper >= 1)
            		{
                		break;
            		} 
            		else
            		{
 				System.out.println("Invalid password! Password should be at least 8 characters long and contain at least one special character,one 						    digit, one lowercase letter, and one uppercase letter.");
            		}
        	}
        	else
        	{
            		System.out.println("Invalid password! Password should be at least 8 characters long and contain at least one special character, one digit, one      					   lowercase letter, and one uppercase letter.");
        	}
    	}

    	System.out.println("=======================================");
    	System.out.println("      REGISTRATION SUCCESSFUL!         ");
    	System.out.println("=======================================");

	}
        
	int login() 
	{
    		System.out.println("=========================================");
    		System.out.println("           ENTER LOGIN DETAILS           ");
    		System.out.println("=========================================");
    		System.out.println("Enter your Registered Email ");
    		String emaill = sc.next();
    		System.out.println("Enter Valid Password ");
    		String pass_wordd = sc.next();
    		int n1;

    		if (emaill.equals(email)) 
    		{
        		if (pass_wordd.equals(password)) 
        		{
            			while (true)
            			{
                    			System.out.println("=====================================");
                    			System.out.println("           LOGIN SUCCESSFUL!         ");
                    			System.out.println("=====================================");
                    			System.out.println("=====================================");
                    			System.out.println("        Choose your sport below:     ");
                    			System.out.println("=====================================");
                    			System.out.println("  1. Cricket                         ");
                    			System.out.println("  2. Volleyball                      ");
                    			System.out.println("  3. Badminton                       ");
                    			System.out.println("  4. Table Tennis                    ");
                    			System.out.println("=====================================");
                    
                    			n1 = sc.nextInt();
                    
                   			if(n1 >= 1 && n1 <= 4)
                    			{	
                        			break;
                    			} 
                    			else 
                    			{
                        			System.out.println("Invalid sport choice! Please choose a valid option.");
                        			System.out.println("Re-direct to choose sport again.....");
                    			}
                		}
            
           			String day;
            			while (true) 
            			{
               				System.out.println("Choose the day you want ");
                			day = sc.next().toLowerCase();
                			if (day.equals("saturday") || day.equals("sunday") || day.equals("monday") || day.equals("tuesday") || day.equals("wednesday") 					    || day.equals("thursday") || day.equals("friday")) 
                			{
                    				break;
                			} 
                			else
                			{
                    				System.out.println("Invalid day! Please enter a valid day.");
                			}
            			}

            			float starting_time = 0;
            			float ending_time = 0;
            			while (true) 
            			{
                			System.out.println("Choose the starting time (in 24-hour format)");
               				starting_time = sc.nextFloat();
                			System.out.println("Choose the ending time (in 24-hour format)");
                			ending_time = sc.nextFloat();
                			if (starting_time >= 9 && ending_time <= 24 && ending_time > starting_time && starting_time % 0.5 == 0 && 
					   ending_time % 0.5 == 0) 
                			{
                    				break;
                			} 
                			else
                			{
                    				System.out.println("Invalid time! Please enter valid starting and ending times.");
                			}
            			}

            			float price = 0;
            			if (day.equals("saturday") || day.equals("sunday")) 
            			{
                			if (n1 == 1) 
                			{
                    				System.out.println("You have chosen cricket ");
                    				price = (ending_time - starting_time) * 1000;
                    				System.out.println("Price for cricket on weekend days: " + price);
                			} 
                			else if (n1 == 2) 
                			{
                    				System.out.println("You have chosen volleyball ");
                    				price = (ending_time - starting_time) * 800;
                    				System.out.println("Price for volleyball on weekends: " + price);
                			} 
                			else if (n1 == 3) 
                			{
                    				System.out.println("You have chosen Badminton ");
                    				price = (ending_time - starting_time) * 800;
                    				System.out.println("Price for Badminton on weekends: " + price);
                			} 
                			else if (n1 == 4) 
                			{
                    				System.out.println("You have chosen Table Tennis ");
                    				price = (ending_time - starting_time) * 800;
                    				System.out.println("Price for Table Tennis on weekends: " + price);
                			}
            			} 
            			else if (day.equals("monday") || day.equals("tuesday") || day.equals("wednesday") || day.equals("thursday") || day.equals("friday"))
            			{
                			if (n1 == 1) 
                			{
                    				System.out.println("You have chosen cricket ");
                    				price = (ending_time - starting_time) * 800;
                    				System.out.println("Price for cricket on normal days: " + price);
                			}
                			else if (n1 == 2) 
                			{
                    				System.out.println("You have chosen volleyball ");
                    				price = (ending_time - starting_time) * 600;
                    				System.out.println("Price for volleyball on normal days: " + price);
                			}
                			else if (n1 == 3) 
                			{
                    				System.out.println("You have chosen Badminton ");
                    				price = (ending_time - starting_time) * 600;
                    				System.out.println("Price for Badminton on normal days: " + price);
                			}
                			else if (n1 == 4) 
                			{
                    				System.out.println("You have chosen Table Tennis ");
                    				price = (ending_time - starting_time) * 1000;
                    				System.out.println("Price for Table Tennis on normal days: " + price);
                			}
            			}

            			return 1;
        		} 
        		else 
        		{
            			System.out.println("Invalid password");
            			return 0;
        		}
    		} 
    		else
    		{
        		System.out.println("Invalid Email");
        		return 0;
    		}
	}
	
	boolean mail(String email)
	{
	        System.out.println("Enter your Email");
	    	this.email=sc.next();
	    	if(email.toLowerCase().endsWith("@gmail.com"))
	    	{
	      		return true;
		}
	    	else 
	    	{
	    		System.out.println("Invalid email!!.Email should be in this Format your email@gmail.com");
	    		return false;
	    	}
	}
	boolean pass1(String password)
	{
	    	int Special = 0;
	    	int Digit = 0;
	    	int Lower = 0;
	    	int Upper = 0;
	    	if (password.length() >= 8) 
	    	{
	    		for (int i = 0; i < password.length(); i++) 
	    		{
	    			char chh = password.charAt(i);
	    			if (chh >= 'a' && chh <= 'z')
	    			{
	    				Lower++;
	    			} 
	    			else if (chh >= 'A' && chh <= 'Z')
	    			{
	    				Upper++;
	    			}
	    			else if (chh >= '0' && chh <= '9')
	    			{
	    				Digit++;
	    			}
	    			else if ("[]!@#$%^&*".indexOf(chh) >= 0) 
	    			{
	    				Special++;
	    			}
	    		}
	    		if (Special>=1 && Digit>=1 && Lower>=1 && Upper>=1) 
	    		{
	    			return true;
	    		}
	    		else
	    		{
	    			return false;
	    		}
	    	}
	    	else
		{
			return false;
		}
	    									    
	}
	void set1(String pass)
	{
		this.password=pass;
	}
	void set2(String email1)
	{
	    this.email=email1;
	}
	String get1()
	{
	    return(password);
	}
	String get2()
	{
		return(email);
	}
	abstract void pay(float a);
}


class Payment extends Project
{
	Scanner scan = new Scanner(System.in);
        static int bank_balance = 10000;

    	void pay(float a) 
	{
        	System.out.println("===========================================");
        	System.out.println("              PAYMENT PROCESS              ");
        	System.out.println("===========================================");
        	System.out.println("Option-1 for PhonePe / GPay / Paytm / Amazon pay");
        	System.out.println("Option-2 for Credit Card");
        	int choose = scan.nextInt();

        	switch (choose)
        	{
            	case 1:
                	UPIPayment();
                	break;
            	case 2:
                	CardPayment();
                	break;
            	default:
                	System.out.println("Invalid Option");
                	break;
        	}
    	}

    	private void UPIPayment() 
    	{ 
    		String upid;
        	while (true) 
        	{
            		System.out.println("Enter beneficiary UPID");
            		upid = scan.next();
            		if (upid.length() == 14 && (upid.endsWith("@ybl") || upid.endsWith("@ibl") || upid.endsWith("@axl"))) 
            		{
                		break;
            		} 
            		else
            		{
                		System.out.println("Wrong UPID, please try again.");
            		}
        	}

        	float a;
       		while (true)
        	{
            		System.out.println("Enter the amount to pay: ");
            		a = scan.nextFloat();
            		if (bank_balance >= a) 
            		{
                		break;
            		}
            		else 
            		{
                		System.out.println("You entered a wrong amount, please try again.");
            		}
        	}
        	while(true)
		{
            		System.out.println("Enter the UPI pin");
            		int upin = scan.nextInt();
            		if (upin >= 1000 && upin <= 9999)
            		{
                		System.out.println("Your payment of " + a + " is done successfully.");
                    		System.out.println("***************************************************");
                    		System.out.println("         BOOKING CONFIRMED NJOY PANDAGOWW!         ");
                    		System.out.println("***************************************************");
                		bank_balance -= a;
                		break;
            		} 
            		else
            		{
                	System.out.println("Entered a wrong UPI pin");
            		}
            }
        }

    	private void CardPayment() 
    	{
        	String card_number;
        	while (true) 
        	{
            		System.out.println("Enter your card number: ");
            	card_number = scan.next();
            	if (card_number.length() == 16) 
		{
                	System.out.println("Valid card number");
                	break;
            	}
            	else 
            	{
                	System.out.println("Invalid card number");
            	}
        }

        String cvv;
        while (true)
        {
            System.out.println("Enter the CVV number: ");
            cvv = scan.next();

            if (cvv.length() == 3 && cvv.matches("\\d{3}"))
            {
            	System.out.println("Valid CVV number");
                break;
            } 
            else
            {
                System.out.println("Invalid CVV number");
            }
        }

        int MM;
        while (true) 
        {
            System.out.println("Enter the card validity (MM/YYYY): ");
            System.out.println("Enter the Month:");
            MM = scan.nextInt();
            
            if (MM >= 1 && MM <= 12) 
            {
                System.out.println("Valid month");
                break;
            }
            else
            {
                System.out.println("Invalid month");
            }
        }
        String YYYY;
        while(true)
        {
            System.out.println("Enter the year:");
            YYYY = scan.next();
            if (YYYY.length() == 4) 
            {
                int expiry_year = Integer.parseInt(YYYY);
                int current_year = LocalDate.now().getYear();
                if (expiry_year >= current_year) 
                {
                    System.out.println("Valid year");
                    break;
                } 
                else 
                {
                    System.out.println("Card has expired, please try again.");
                }
            } 
            else
            {
                System.out.println("Invalid year format, please try again.");
            }
        }

        String mobile_number;
        while (true)
        {
            System.out.println("Enter mobile number: ");
            mobile_number = scan.next();
            if (isMobileNumberValid(mobile_number)) 
            {
                System.out.println("Valid mobile number");
                break;
            } 
            else 
            {
                System.out.println("Invalid mobile number, please try again.");
            }
        }

        int price;
        System.out.println("Enter the amount to pay: ");
        price = sc.nextInt();
        int otp=0;
        int min = 1000;
        int max = 9999;
        Random rand = new Random();
        int random = rand.nextInt(max - min + 1) + min;
        System.out.println("Generated random number: " + random);

        int opp=0;
        while (opp<3) 
        {
            System.out.print("Enter OTP: ");
            otp = scan.nextInt();
            if (random == otp) 
            {
                if (price <= bank_balance) 
                {
                    System.out.println("Your payment of " + price + " is done successfully.");
                    System.out.println("***************************************************");
                    System.out.println("         BOOKING CONFIRMED NJOY PANDAGOWW!         ");
                    System.out.println("***************************************************");
                    bank_balance -= price;
                    break;
                } 
                else
                {
                    System.out.println("Insufficient balance in your account.");
                    break;
                }
            } 
            else
            {
                if(opp==2)
		{
                    System.out.println("You are trying too many attempts");
                }
                System.out.println("Invalid OTP, please try again.");
                opp++;
            }
        }
        if(otp != random)
	{
            CardPayment();
        }
    }
}


public class User extends Payment
{
        public static void main(String[] args) 
	{
		Scanner sc = new Scanner(System.in);
		Payment obj = new User();
        	int c = 0;
        	while (c == 0) 
       		{
			System.out.println("=======================================");
                	System.out.println("          WELCOME TO OUR TURF          ");
                	System.out.println("=======================================");
                	System.out.println("  Are you a new user? Choose Option 1  ");
                	System.out.println("  1. Register                          ");
                	System.out.println("  2. Login                             ");
                	System.out.println("=======================================");
                	int n = obj.sc.nextInt();
	        	switch (n) 
	        	{
				case 1:
	                        obj.register();
	                        break;
	                    case 2:
	                    	c = obj.login();
	                        if (c == 1) 
	                        {
	                            System.out.println("=======================================");
                                System.out.println("    Would you like to make a payment?  ");
                                System.out.println("=======================================");
                                System.out.println("  1. Make a Payment                    ");
                                System.out.println("  2. Logout                            ");
                                System.out.println("=======================================");
	                            int n2 = obj.sc.nextInt();
	                            if (n2 == 1)
	                            {
	                                obj.pay(c);
	                                
	                            } 
	                            else if (n2 == 2) 
	                            {
	                                System.out.println("Logged out.");
	                                c = 0;
	                            }
	                        } 
	                        else
	                        {
	                        	System.out.println("=======================================");
                                	System.out.println("       Choose your next option:        ");
                                	System.out.println("=======================================");
                                	System.out.println("  1. Forget Password                   ");
                                	System.out.println("  2. Email Update                      ");
                                	System.out.println("  3. Home                              ");
                                	System.out.println("=======================================");
	                            	int n1 = obj.sc.nextInt();
	                            	switch (n1) 
	                            	{
	                                	case 1:
	                                    		System.out.print("Enter the new password: ");
	                                    		String pass = obj.sc.next();
	                                    		System.out.println("Confirm password");
	                                    		String conf_pass = obj.scan.next();
	                                    		while(true) {
	                                    			if(pass.equals(conf_pass) && obj.pass1(pass))
	                                    			{
			                                        		obj.set1(pass);
			                                        		System.out.println("Password updated: " + obj.get1());	
			                                        		break;
	                                    			}
		                                    		else 
		                                    		{
		                                    			System.out.println("Password didn't match");
		                                    		}
	                                    		}	
	                                    		break;
	                                	case 2:
	                                    		System.out.print("Enter the email: ");
	                                    		String email1 = obj.sc.next();
	                                    		System.out.println("Confirm email");
	                                    		String conf_email = obj.scan.next();
	                                    		while(true)
	                                    		{
	                                    			if(email1.equals(conf_email) && obj.mail(email1))
		                                    		{
			                                        	obj.set2(email1);
			                                        	System.out.println("Email updated: " + obj.get2());
			                                        	break;
		                                    		}
		                                    		else 
		                                    		{
		                                    			System.out.println("Email didn't match");
		                                    		}
	                                    		}
	                                    		break;
	                                	case 3:
	                                    		break;
	                                	default:
	                                    		System.out.println("Enter the valid option");
	                                    		break;
	                            	}
	                        }
	                        break;
	                    default:
	                        System.out.println("Enter the valid option");
	                        break;
	               }
	              	    
	        }
	 }
}
