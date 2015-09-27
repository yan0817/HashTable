# HashTable
// Yanni Angelides
// Creating a basic hash table object

import java.lang.Math;

public class HashTable
{
  private int capacity = .6;
	private int size;
	private Object[] arr;
	private int numOfOccupiedSpaces = 0;
	
	public HashTable
	{
		arr = new Object[100];
		size = 100;
	}
	
	public void put(Object obj)
	{
		String sObj = obj.toString();
		int i = 0;
		int total = 0;
		while (i < sObj.length())
		{
			char a = sObj.charAt(i);
			total += (int)a	
		}
		int spot = total % size
		while(arr[spot] != 0)
		{
			spot++;
		}
		arr[spot] = total;
		numOfOccupiedSpaces++;
		if ((numOfOccupiedSpaces/size) >= .6)
			rehash(); 
	}
	
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
	
	public String toString()
	{
		String strOfArr = "";
		for (int i = 0; i < arr.length; i++)
		{
			strOfArr += arr[i].toString() + ", ";	
		}
	}
}
