// Decimal Converter - Convert a binary number to its decimal equivalent.

import java.util.concurrent.ThreadLocalRandom;

public class DecimalConverter {
	
	static double decimalToBinary(String bin)
	{
		// read the string from right to left, add 2^i for each char
		double dec = 0;

		for (int i = 0; i < bin.length()-1; i++)
		{		
			int exponent = Integer.parseInt(Character.toString(bin.charAt((bin.length()-i)-1)));
			
			dec = dec + (exponent * Math.pow(2,(i)));
		}
		return  dec;
	}
	
	// create a random binary string of length 1-10, 50-50 chance 1 or 0
	static String genBinary()
	{
		String bin = "";
		int randomBinLength = ThreadLocalRandom.current().nextInt(1, 11);
		
		for (int i = randomBinLength; i >= 0; i--)
		{
			int randomBinVal = ThreadLocalRandom.current().nextInt(0, 2);
			String binString = Integer.toString(randomBinVal);
			bin = bin.concat(binString);		
		}

		return bin;
	}

	public static void main(String[] args) 
	{
		String bin = genBinary();
		System.out.println("Binary Sting: " + bin);
		System.out.println("Dec Value: " + decimalToBinary(bin));
	}
}
