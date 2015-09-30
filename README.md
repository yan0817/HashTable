# HashTable
/**
For this project we were asked to create a simple hash table object that allows a user to input an object of his or her choice to the hash table
@author Yanni Angelides
@ version 09/29/15
*/

public class HashTable
{
	private double capacity = .6;
	private int size;
	private Object[] arr;
	private int numOfOccupiedSpaces = 0;
	private int quadProb = 1;
	
	public HashTable()
	{
		arr = new Object[100];
		size = 100;
	}
	
	/**
	@ param obj Object that represents the Object the user wants to put in the hash table
	@ return puts object taken in as a parameter in the correct spot in the hash table based on the hash function 
	*/
	public void put(Object obj)
	{
		String sObj = obj.toString();
		int i = 0;
		int total = 0;
		while (i < sObj.length())
		{
			char a = sObj.charAt(i);
			total += (int)a;	
		}
		int spot = total % size;
		while(arr[spot] != null)
		{
			spot=spot*2;
			quadProb=quadProb*2;
		}
		spot = spot % size;
		arr[spot] = total;
		numOfOccupiedSpaces++;
		if ((numOfOccupiedSpaces/size) >= .6)
			rehash(); 
	}
	
	/**
	Creates a new array that is double the size of the old array and copies all the values of the old
	array into the new one
	@param null
	@return creates a new array of double the size
	*/
	private void rehash()
	{
		Object[] arrCopy = new Object[size*2];
		int i = 0;
		while (i < arr.length)
		{
			arrCopy[i] = arr[i];
		}
		arr = arrCopy;
	}
	
	/**
	Takes the the hash table array and turns the values into a string.
	@param null
	@return returns a string representation of the hash table array
	*/
	public String toString()
	{
		String strOfArr = "";
		for (int i = 0; i < arr.length; i++)
		{
			strOfArr += arr[i].toString() + ", ";	
		}
		return strOfArr;
	}
	
	public static void main(String [] args)
	{
		HashTable table = new HashTable();
		table.put("Asbds");
		table.put("hdjfsk");
		table.put("jkrkjs");
		table.put("dfsadsa");
		table.toString();
	}
}
