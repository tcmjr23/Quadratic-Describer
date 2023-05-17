# Quadratic-Describer
This project asks the user to input values for the coefficients a, b, and c. It then uses those values in calculating the quadratic equation , as well as providing all of the details of its graph.
Here are key code samples from the project:


# public class QuadraticClient {
	public static void main(String[] args) {
		//Greeting
		//Loop (while)
			//get input from user
			//call quadrDescriber() to analyze the
			//print the results
			//ask --go again?
			//get answer
		Scanner userImput = new Scanner(System.in);
		boolean prog = true;
		do{
			System.out.println("Welcome to the Quadratic Describer");
			System.out.println("Provide values for the coefficients a, b, and c");
			System.out.println("");
			System.out.print("a: ");
			double a = userImput.nextInt();
			System.out.print("b: ");
			double b = userImput.nextInt();
			System.out.print("c: ");
			double c = userImput.nextInt();
			System.out.println("");
			System.out.println("Description of the graph of:");
			System.out.println(Quadratic.quadrDescriber(a,b,c));
			System.out.println();
		
			System.out.println("do you want to keep going? (Type \"quit\" to end)");
			System.out.print("Response: ");
			String response = userImput.next();
			if (response.equals("quit")) {
				prog = false;
				}
			}while(prog == true);
		userImput.close();
	}
}

This include the main method of the class QuadraticClient. It uses a scanner to process the user's inputs. The user is first prompted to provide their name, then it asks for the 3 coefficient value. It then calls the quadrDescriber method from the Quadratic class, detailed below. It then asks the user if they would like to go again.

# public static String quadrDescriber (double a, double b, double c) {
		
		String answer = "y = " + a + "^2 + " + b + " x + " + c;
		String newLine = "\n";
		String conc = "\n"; 
    
		if (a >= 0) {
			conc = "\nOpens: Up";
		}
		else {
			conc = "\nOpens: Down";
		}
		
		double symmetry = round2(-b/2*a);
		String Symmetry = "\nAxis of Symmetry: " + symmetry;
		double vertex = a*round2(-b/2*a)*round2(-b/2*a) + b*round2(-b/2*a)+c;
		String xInt = "\nx-intercept(s): " + (quadForm((int) a,(int) b,(int) c)); 
		double yInt = c;
		return answer + newLine + conc + Symmetry + newLine + "Vertex: (" + symmetry + ", " + vertex + ")" + xInt + newLine + "y-intercept: " + yInt; 
	}

This method within the Quadratic class takes in the values of the coefficients passed and then calls other methods within the class to analyze the vertex, x intercept, y intercept, direction in which it opens, as well as providing the fully formatted quadratic equation. 

# public static String quadForm(int a, int b, int c) {
		double discriminant = discriminant(a,b,c);
		if(discriminant<0) {
			return "no real roots";
		} else if(discriminant == 0) {
			double oneRoot = ((-1*b)/(2*a));
			return oneRoot+"";
		}else {
			double plus = round2((-1*b + sqrt(discriminant))/(2*a));
			double minus = round2((-1*b - sqrt(discriminant))/(2*a));
			double max = max(plus,minus);
			double min = min(minus,plus);
			return absValue(max) + " and " + -max;
		}
	}
	
This method puts the coefficients into the quadratic formula. 

# public static double discriminant(double a, double b, double c) {
		return (b*b-4*(a*c));
   }
This method calculates and returns the discriminant of the coeeficients

# public static double sqrt(double n) {
		double a = n;
		for(int i=1; i<=n; i++) {
			a = (0.5*(n/a+a));}
			a = round2(a);
			return a;
   }
 This method calculates the square root of the discriminant which is used to calculate the quadratic equation. 
 
