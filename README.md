# Lab-7_202001177
## Section-A
**Based on the input ranges, we can identify the following equivalence classes:** <br>

**Equivalence Class Partitions** <br/>
Day:
| Partition ID | Range | Status |
|----------------------|-------|--------|
| E1 | Between 1 and 28 | Valid |
| E2 | Less than 1 | Invalid |
| E3 | Greater than 31 | Invalid |
| E4 | Equals 30 | Valid |
| E5 | Equals 29 | Valid for leap year |
| E6 | Equals 31 | Valid |

Month:
| Partition ID | Range | Status |
|----------------------|-------|--------|
| E7 | Between 1 and 12 | Valid |
| E8 | Less than 1 | Invalid |
| E9 | Greater than 12 | Invalid |

Year: 
| Partition ID | Range | Status |
|----------------------|-------|--------|
| E10 | Between 1900 and 2015 | Valid |
| E11 | Less than 1900 | Invalid |
| E12 | Greater than 2015 | Invalid |

**Equivalence Partitioning Test Cases:**

<table>
  <tr>
    <th>Tester Action and Input Data</th>
    <th>Expected Outcome</th>
  </tr>
  <tr>
    <td>Valid input: day=31, month=12, year=2015</td>
    <td>Previous date</td>
  </tr>
  <tr>
    <td>Invalid input: day=0, month=10, year=2010</td>
    <td>An error message</td>
  </tr>
  <tr>
    <td>Valid input: day=1, month=1, year=1900</td>
    <td>Invalid date</td>
  </tr>
  <tr>
    <td>Invalid input: day=29, month=2, year=2003</td>
    <td>An error message</td>
  </tr>
  <tr>
    <td>Invalid input: day=32, month=5, year=2010</td>
    <td>An error message</td>
  </tr>
  
</table>

<br>

**Boundary Value Analysis:**  <br>
In boundary value analysis, we check for input values near the boundaries of valid and invalid values that are more likely to cause errors, so testing these boundary values can help identify potential problems in the software.<br>

We first identify the boundary values for day, month, and year <br>
<br>
***Day***: 1, 28, 29, 30, 31  <br>
***Month***: 1, 2, 12         <br>
***Year***: 1, 4, 100, 400 (for checking Leap Years). <br>
<br>

We then find valid and invalid input ranges for day, month, and year <br>
<br>
***Day***: valid input range is from 1 to 31, invalid input range is from 32 to infinity. <br>
***Month***: valid input range is from 1 to 12, invalid input range is from 13 to infinity. <br>
***Year***: valid input range is from 1900 to 2015, invalid range is anything outside that range. <br>
<br>

Using these to sample generate test cases: <br>
***Test case 1***: Valid date (boundary value) - Day: 1, Month: 1, Year: 2010 <br>
***Test case 2***: Valid date (boundary value) - Day: 31, Month: 12, Year: 2010 <br>
***Test case 3***: Valid date (boundary value) - Day: 29, Month: 2, Year: 2000 (leap year)  <br>
***Test case 4***: Invalid date (boundary value) - Day: 32, Month: 1, Year: 1990  <br>
***Test case 5***: Invalid date (boundary value) - Day: 13, Month: 2, Year: 1910  <br>
***Test case 6***: Invalid date (boundary value) - Day: 30, Month: 2, Year: 1930  <br>
***Test case 7***: Invalid date (boundary value) - Day: 31, Month: 4, Year: 1930  <br>
***Test case 8***: Valid date (within valid range) - Day: 15, Month: 6, Year: 2015  <br>
***Test case 9***: Invalid date (day is outside valid range) - Day: 32, Month: 6, Year: 2010  <br>
***Test case 10***: Invalid date (month is outside valid range) - Day: 15, Month: 13, Year: 2010  <br>
***Test case 11***: Invalid date (year is outside valid range) - Day: 15, Month: 6, Year: 2030  <br>
<br>

### P1. The function linearSearch searches for a value v in an array of integers a. If v appears in the array a, then the function returns the first index i, such that a[i] == v; otherwise, -1 is returned.

Program 1 that we are testing : <br>
<br>
```
package tests;

public class allPrograms {
	
	int linearSearch(int v, int a[])
	{
		int i = 0;
		while (i < a.length)
		{
			if (a[i] == v)
				return(i);
			i++;
		}
		return (-1);
	}
	
}
```
<br>
JUnit Testing for Program 1: 
<br>

```
package tests;

import static org.junit.Assert.*;

import org.junit.Test;

public class P1_linearSearch_tests {

	@Test
	public void test1() {
		int arr[] = { 5, 4, 3, 1, 2 };
		
		allPrograms program = new allPrograms();
		int result = program.linearSearch(1, arr);
		
		System.out.println(result);
		assertEquals(3, result);
	}
	
	@Test
	public void test2() {
		int arr[] = { };
		
		allPrograms program = new allPrograms();
		int result = program.linearSearch(1, arr);
		
		System.out.println(result);
		assertEquals(-1, result);
	}
	
	@Test
	public void test3() {
		int arr[] = { 1 };
		
		allPrograms program = new allPrograms();
		int result = program.linearSearch(1, arr);
		
		System.out.println(result);
		assertEquals(0, result);
	}
	
	@Test
	public void test4() {
		int arr[] = { 10 };
		allPrograms program = new allPrograms();
		int result = program.linearSearch(1, arr);
		
		System.out.println(result);
		assertEquals(-1, result);
	}
	
	@Test
	public void test5() {
		int arr[] = { 5, 4, 3, 1, 2 };
		
		allPrograms program = new allPrograms();
		int result = program.linearSearch(10, arr);
		
		System.out.println(result);
		assertEquals(-1, result);
	}

}
```
 
**Equivalence Partitioning:**

<table>
  <thead>
    <tr>
      <th>Tester Action and Input Data</th>
      <th>Expected Outcome</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Test with v as a non-existent value and an empty array a[]</td>
      <td>-1</td>
    </tr>
    <tr>
      <td>Test with v as a non-existent value and a non-empty array a[]</td>
      <td>-1</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an empty array a[]</td>
      <td>-1</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and a non-empty array a[] where v exists</td>
      <td>the index of v in a[]</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and a non-empty array a[] where v does not exist</td>
      <td>-1</td>
    </tr>
  </tbody>
</table>

**Boundary Value Analysis:**

<table>
  <thead>
    <tr>
      <th>Tester Action and Input Data</th>
      <th>Expected Outcome</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Test with v as a non-existent value and an empty array a[]</td>
      <td>-1</td>
    </tr>
    <tr>
      <td>Test with v as a non-existent value and a non-empty array a[]</td>
      <td>-1</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an array a[] of length 0</td>
      <td>-1</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an array a[] of length 1, where v exists</td>
      <td>0</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an array a[] of length 1, where v does not exist</td>
      <td>-1</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an array a[] of length greater than 1, where v exists at the beginning of the array</td>
      <td>0</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an array a[] of length greater than 1, where v exists at the end of the array</td>
      <td>the last index where v is found</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an array a[] of length greater than 1, where v exists in the middle of the array</td>
      <td>the index where v is found</td>
    </tr>
  </tbody>
</table>
</br>

### P2. The function countItem returns the number of times a value v appears in an array of integers a.
    
```
    int countItem(int v, int a[])
    {
        int count = 0;
        for (int i = 0; i < a.length; i++)
            {
                if (a[i] == v)
                count++;
            }
        return (count);
    }
```
JUnit Testing for Program 2: 
<br>

```
package tests;

import static org.junit.Assert.*;

import org.junit.Test;

public class P2_countItem_tests {

	@Test
	public void test1() {
		int arr[] = {  };
		allPrograms program = new allPrograms();
		int result = program.countItem(10, arr);
		
		assertEquals(result, 0);
	}
	
	@Test
	public void test2() {
		int arr[] = { 10, 10, 20, 30, 10 };
		allPrograms program = new allPrograms();
		int result = program.countItem(5, arr);
		
		assertEquals(result, 0);
	}
	
	@Test
	public void test3() {
		int arr[] = { 10, 10, 20, 30, 10 };
		allPrograms program = new allPrograms();
		int result = program.countItem(10, arr);
		
		assertEquals(result, 3);
	}
	
	@Test
	public void test4() {
		int arr[] = { 10, 10, 20, 30, 10 };
		allPrograms program = new allPrograms();
		int result = program.countItem(20, arr);
		
		assertEquals(result, 1);
	}
	
	@Test
	public void test5() {
		int arr[] = { 10 };
		allPrograms program = new allPrograms();
		int result = program.countItem(10, arr);
		
		assertEquals(result, 1);
	}
	
	@Test
	public void test6() {
		int arr[] = { 10 };
		allPrograms program = new allPrograms();
		int result = program.countItem(20, arr);
		
		assertEquals(result, 0);
	}
	
	@Test
	public void test7() {
		int arr[] = { 1, 1, 2, 3, 1, 1, 1 };
		allPrograms program = new allPrograms();
		int result = program.countItem(1, arr);
		
		assertEquals(result, 5);
	}
}
	
```
<br>


**Equivalence Partitioning:**

<table>
  <thead>
    <tr>
      <th>Tester Action and Input Data</th>
      <th>Expected Outcome</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Test with v as a non-existent value and an empty array a[]</td>
      <td>0</td>
    </tr>
    <tr>
      <td>Test with v as a non-existent value and a non-empty array a[]</td>
      <td>0</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an empty array a[]</td>
      <td>0</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and a non-empty array a[] where v exists multiple times</td>
      <td>the number of occurrences of v in a[]</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and a non-empty array a[] where v exists only once</td>
      <td>1</td>
    </tr>
  </tbody>
</table>

**Boundary Value Analysis:**

<table>
  <thead>
    <tr>
      <th>Tester Action and Input Data</th>
      <th>Expected Outcome</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Test with v as a non-existent value and an empty array a[]</td>
      <td>0</td>
    </tr>
    <tr>
      <td>Test with v as a non-existent value and a non-empty array a[]</td>
      <td>0</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an array a[] of length 0</td>
      <td>0</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an array a[] of length 1, where v exists</td>
      <td>1</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an array a[] of length 1, where v does not exist</td>
      <td>0</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an array a[] of length greater than 1, where v exists at the beginning of the array</td>
      <td>the number of occurrences of v in a[]</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an array a[] of length greater than 1, where v exists at the end of the array</td>
      <td>the number of occurrences of v in a[]</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an array a[] of length greater than 1, where v exists in the middle of the array</td>
      <td>the number of occurrences of v in a[]</td>
    </tr>
  </tbody>
</table>
</br>
 
 

### P3. The function binarySearch searches for a value v in an ordered array of integers a. If v appears in the array a, then the function returns an index i, such that a[i] == v; otherwise, -1 is returned.
Assumption: the elements in the array a are sorted in non-decreasing order.

```
    int binarySearch(int v, int a[])
    {
        int lo,mid,hi;
        lo = 0;
        hi = a.length-1;
        while (lo <= hi)
        {
            mid = (lo+hi)/2;
            if (v == a[mid])
            return (mid);
            else if (v < a[mid])
            hi = mid-1;
            else
            lo = mid+1;
        }
        return(-1);
    }
   ```
JUnit Testing for Program 3:
<br>
   ```
package tests;

import static org.junit.Assert.*;

import org.junit.Test;

public class P3_binarySearch_tests {

	@Test
	public void test1() {
		int arr[] = { 1,2,3,4,5 };
		allPrograms program = new allPrograms();
		int result = program.binarySearch(3, arr);
		
		assertEquals(2, result);
	}
	
	@Test
	public void test2() {
		int arr[] = { 1,2,3,4,5 };
		allPrograms program = new allPrograms();
		int result = program.binarySearch(1, arr);
		
		assertEquals(0, result);
	}
	
	@Test
	public void test3() {
		int arr[] = { 1,2,3,4,5 };
		allPrograms program = new allPrograms();
		int result = program.binarySearch(5, arr);
		
		assertEquals(4, result);
	}
	
	@Test
	public void test4() {
		int arr[] = { 1,2,3,4,5 };
		allPrograms program = new allPrograms();
		int result = program.binarySearch(6, arr);
		
		assertEquals(-1, result);
	}
	
	@Test
	public void test5() {
		int arr[] = { 1 };
		allPrograms program = new allPrograms();
		int result = program.binarySearch(1, arr);
		
		assertEquals(0, result);
	}
	
	@Test
	public void test6() {
		int arr[] = {  };
		allPrograms program = new allPrograms();
		int result = program.binarySearch(1, arr);
		assertEquals(-1, result);
	}
				
	@Test
	public void test7() {
		int arr[] = { 1, 2, 3 };
		allPrograms program = new allPrograms();
		int result = program.binarySearch(3, arr);
			
		assertEquals(2, result);
	}

}

```
**Equivalence Partitioning:**

<table>
  <tr>
    <th>Tester Action and Input Data</th>
    <th>Expected Outcome</th>
  </tr>
  <tr>
    <td>v=3, a=[1 , 2 , 3 , 4 , 5]</td>
    <td>2</td>
  </tr>
  <tr>
    <td>v=1, a=[1 , 2 , 3 , 4 , 5]</td>
    <td>0</td>
  </tr>
  <tr>
    <td>v=5, a=[1 , 2 , 3 , 4 , 5]</td>
    <td>4</td>
  </tr>
  <tr>
    <td>v=6, a=[1 , 2 , 3 , 4 , 5]</td>
    <td>-1</td>
  </tr>
  <tr>
    <td>v=1, a=[1]</td>
    <td>0</td>
  </tr>
  <tr>
    <td>v=1, a=[]</td>
    <td>-1</td>
  </tr>
	<tr>
    <td>v=3, a=[1 , 2 , 3]</td>
    <td>2</td>
  </tr>
	
</table>

**Boundary Value Analysis:**

<table>
  <tr>
    <th>Tester Action and Input Data</th>
    <th>Expected Outcome</th>
  </tr>
  <tr>
    <td>v=1, a=[1]</td>
    <td>0</td>
  </tr>
  <tr>
    <td>v=6, a=[]</td>
    <td>-1</td>
  </tr>
  <tr>
    <td>v=1, a=[1, 2, 3]</td>
    <td>0 (smallest element in the array)</td>
  </tr>
  <tr>
    <td>v=3, a=[1, 2, 3]</td>
    <td>2 (largest element in the array)</td>
  </tr>
</table>
</br>


### P4. The following problem has been adapted from The Art of Software Testing, by G. Myers (1979). The function triangle takes three integer parameters that are interpreted as the lengths of the sides of a triangle. It returns whether the triangle is equilateral (three lengths equal), isosceles (two lengths equal), scalene (no lengths equal), or invalid (impossible lengths).
```
    final int EQUILATERAL = 0;
    final int ISOSCELES = 1;
    final int SCALENE = 2;
    final int INVALID = 3;
    int triangle(int a, int b, int c)
    {
        if (a >= b+c || b >= a+c || c >= a+b)
        return(INVALID);
        if (a == b && b == c)
        return(EQUILATERAL);
        if (a == b || a == c || b == c)
        return(ISOSCELES);
        return(SCALENE);
    }
```
JUnit Testing for Program 4: 
<br>

```
package tests;

import static org.junit.Assert.*;

import org.junit.Test;

public class P4_triangle_tests {

	@Test
	public void test1() {
		int a = 2, b = 2, c = 2;
		allPrograms program = new allPrograms();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 0);
	}
	@Test
	public void test2() {
		int a = 3, b = 3, c = 4;
		allPrograms program = new allPrograms();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 1);
	}
	@Test
	public void test3() {
		int a = 6, b = 5, c = 4;
		allPrograms program = new allPrograms();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 2);
	}
	@Test
	public void test4() {
		int a = 0, b = 0, c = 0;
		allPrograms program = new allPrograms();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 3);
	}
	@Test
	public void test5() {
		int a =-1, b =-1, c = 5;
		allPrograms program = new allPrograms();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 3);
	}
	@Test
	public void test6() {
		int a = 2, b = 2, c = 1;
		allPrograms program = new allPrograms();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 1);
	}
	@Test
	public void test7() {
		int a = 0, b = 1, c = 1;
		allPrograms program = new allPrograms();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 3);
	}
	@Test
	public void test8() {
		int a = 1, b = 0, c = 1;
		allPrograms program = new allPrograms();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 3);
	}
	@Test
	public void test9() {
		int a = 1, b = 1, c = 0;
		allPrograms program = new allPrograms();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 3);
	}
	@Test
	public void test10() {
		int a = 1, b = 2, c = 3;
		allPrograms program = new allPrograms();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 3);
	}
	@Test
	public void test11() {
		int a = 3, b = 1, c = 3;
		allPrograms program = new allPrograms();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 1);
	}
	@Test
	public void test12() {
		int a = 5, b = 4, c = 2;
		allPrograms program = new allPrograms();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 2);
	}
	@Test
	public void test13() {
		int a = Integer.MAX_VALUE, b = Integer.MAX_VALUE, c = Integer.MAX_VALUE;
		allPrograms program = new allPrograms();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 3);
	}
}
``` 
 
 **Equivalence Partitioning:**

<table>
  <tr>
    <th>Tester Action and Input Data</th>
    <th>Expected Outcome</th>
  </tr>
  <tr>
    <td>Valid input: a=2, b=2, c=2</td>
    <td>0</td>
  </tr>
  <tr>
    <td>Valid input: a=3, b=3, c=4</td>
    <td>1</td>
  </tr>
  <tr>
    <td>Valid input: a=6, b=5, c=4</td>
    <td>2</td>
  </tr>
  <tr>
    <td>Invalid input: a=0, b=0, c=0</td>
    <td>3</td>
  </tr>
  <tr>
    <td>Invalid input: a=-1, b=-1, c=5</td>
    <td>3</td>
  </tr>
  <tr>
    <td>Valid input: a=1, b=1, c=1</td>
    <td>0</td>
  </tr>
  <tr>
    <td>Valid input: a=2, b=2, c=1</td>
    <td>1</td>
  </tr>
  <tr>
    <td>Valid input: a=3, b=4, c=5</td>
    <td>2</td>
  </tr>
  <tr>
    <td>Invalid input: a=0, b=1, c=1</td>
    <td>3</td>
  </tr>
  <tr>
    <td>Invalid input: a=1, b=0, c=1</td>
    <td>3</td>
  </tr>
  <tr>
    <td>Invalid input: a=1, b=1, c=0</td>
    <td>3</td>
  </tr>
</table>
</br>

**Boundary Value Analysis:**
<table>
  <tr>
    <th>Tester Action and Input Data</th>
    <th>Expected Outcome</th>
  </tr>
  <tr>
    <td>Invalid inputs: a = 0, b = 0, c = 0</td>
    <td>3</td>
  </tr>
  <tr>
    <td>Invalid inputs: a + b = c or b + c = a or c + a = b (a=3, b=4, c=8)</td>
    <td>3</td>
  </tr>
  <tr>
    <td>Equilateral triangles: a = b = c = 1</td>
    <td>0</td>
  </tr>
  <tr>
    <td>Isosceles triangles: a = b ≠ c = 10</td>
    <td>1</td>
  </tr>
  <tr>
    <td>Scalene triangles: a = b + c - 1</td>
    <td>2</td>
  </tr>
  <tr>
    <td>Scalene triangles: b = a + c - 1</td>
    <td>2</td>
  </tr>
  <tr>
    <td>Scalene triangles: c = a + b - 1</td>
    <td>2</td>
  </tr>
  <tr>
    <td>Maximum values: a, b, c = Integer.MAX_VALUE</td>
    <td>3</td>
  </tr>
  <tr>
    <td>Minimum values: a, b, c = Integer.MIN_VALUE</td>
    <td>3</td>
  </tr>
</table>
<br>

### P5. The function prefix (String s1, String s2) returns whether or not the string s1 is a prefix of string s2 (you may assume that neither s1 nor s2 is null).
 ```
    public static boolean prefix(String s1, String s2)
    {
        if (s1.length() > s2.length())
        {
            return false;
        }

        for (int i = 0; i < s1.length(); i++)
        {
            if (s1.charAt(i) != s2.charAt(i))
            {
                return false;
            }
        }
        return true;
    }
```

JUnit Testing for Program 5: 
<br>

```
package tests;

import static org.junit.Assert.*;

import org.junit.Test;

public class P5_prefix_tests {

	@Test
	public void test1() {
		String str1 = "good", str2 = "good morning";
		
		allPrograms program = new allPrograms();
		boolean result = program.prefix(str1, str2);
		
		assertEquals(result, true);
	}
	@Test
	public void test2() {
		String str1 = "a", str2 = "abc";
		
		allPrograms program = new allPrograms();
		boolean result = program.prefix(str1, str2);
		
		assertEquals(result, true);
	}
	@Test
	public void test3() {
		String str1 = "", str2 = "good morning";
		
		allPrograms program = new allPrograms();
		boolean result = program.prefix(str1, str2);
		
		assertEquals(result, true);
	}
	@Test
	public void test4() {
		String str1 = "morning", str2 = "good morning";
		
		allPrograms program = new allPrograms();
		boolean result = program.prefix(str1, str2);
		
		assertEquals(result, false);
	}
	@Test
	public void test5() {
		String str1 = "soft", str2 = "software";
		
		allPrograms program = new allPrograms();
		boolean result = program.prefix(str1, str2);
		
		assertEquals(result, true);
	}
	@Test
	public void test6() {
		String str1 = "software", str2 = "soft";
		
		allPrograms program = new allPrograms();
		boolean result = program.prefix(str1, str2);
		
		assertEquals(result, false);
	}
	@Test
	public void test7() {
		String str1 = "a", str2 = "ab";
		
		allPrograms program = new allPrograms();
		boolean result = program.prefix(str1, str2);
		
		assertEquals(result, true);
	}
	@Test
	public void test8() {
		String str1 = "software", str2 = "softwareee";
		
		allPrograms program = new allPrograms();
		boolean result = program.prefix(str1, str2);
		
		assertEquals(result, true);
	}
	@Test
	public void test9() {
		String str1 = "abc", str2 = "abc";
		
		allPrograms program = new allPrograms();
		boolean result = program.prefix(str1, str2);
		
		assertEquals(result, true);
	}
	@Test
	public void test10() {
		String str1 = "a", str2 = "b";
		
		allPrograms program = new allPrograms();
		boolean result = program.prefix(str1, str2);
		
		assertEquals(result, false);
	}
	@Test
	public void test11() {
		String str1 = "a", str2 = "a";
		
		allPrograms program = new allPrograms();
		boolean result = program.prefix(str1, str2);
		
		assertEquals(result, true);
	}
	@Test
	public void test12() {
		String str1 = "", str2 = "";
		
		allPrograms program = new allPrograms();
		boolean result = program.prefix(str1, str2);
		
		assertEquals(result, true);
	}
}
```

**Equivalence Partitioning:**

<table>
  <tr>
    <th>Tester Action and Input Data</th>
    <th>Expected Outcome</th>
  </tr>
  <tr>
    <td>Valid Inputs: s1 = "good", s2 = "good morning"</td>
    <td>true</td>
  </tr>
  <tr>
    <td>Valid Inputs: s1 = "a", s2 = "abc"</td>
    <td>true</td>
  </tr>
  <tr>
    <td>Invalid Inputs: s1 = "", s2 = "good morning"</td>
    <td>false</td>
  </tr>
  <tr>
    <td>Invalid Inputs: s1 = "morning", s2 = "good morning"</td>
    <td>false</td>
  </tr>
</table>

<br>

**Boundary Value Analysis:**

<table>
  <tr>
    <th>Tester Action and Input Data</th>
    <th>Expected Outcome</th>
  </tr>
  <tr>
    <td>s1 = "", s2 = "software"</td>
    <td>True</td>
  </tr>
  <tr>
    <td>s1 = "soft", s2 = "software"</td>
    <td>True</td>
  </tr>
  <tr>
    <td>s1 = "software", s2 = "soft"</td>
    <td>False</td>
  </tr>
  <tr>
    <td>s1 = "a", s2 = "ab"</td>
    <td>True</td>
  </tr>
  <tr>
    <td>s1 = "software", s2 = "softwareefdfeee"</td>
    <td>True</td>
  </tr>
  <tr>
    <td>s1 = "abc", s2 = "abc"</td>
    <td>True</td>
  </tr>
  <tr>
    <td>s1 = "a", s2 = "b"</td>
    <td>False</td>
  </tr>
  <tr>
    <td>s1 = "a", s2 = "a"</td>
    <td>True</td>
  </tr>
  <tr>
    <td>s1 = "a", s2 = "b"</td>
    <td>False</td>
  </tr>
  <tr>
    <td>s1 = "a", s2 = " "</td>
    <td>False</td>
  </tr>

  <tr>
    <td>s1 = "", s2 = ""</td>
    <td>True</td>
  </tr>
</table>
</br>
<br>

### P6: Consider again the triangle classification program (P4) with a slightly different specification: The programreads floating values from the standard input. The three values A, B, and C are interpreted asrepresenting the lengths of the sides of a triangle. The program then prints a message to the standard output that states whether the triangle, if it can be formed, is scalene, isosceles, equilateral, or right angled. Determine the following for the above program:

**a) Identify the equivalence classes for the system**
Equivalence Classes:<br>
EC1: Invalid inputs (negative or zero values)<br>
EC2: Non-triangle (sum of the two shorter sides is not greater than the longest side)<br>
EC3: Scalene triangle (no sides are equal)<br>
EC4: Isosceles triangle (two sides are equal)<br>
EC5: Equilateral triangle (all sides are equal)<br>
EC6: Right-angled triangle (satisfies the Pythagorean theorem)<br>

**b) Identify test cases to cover the identified equivalence classes. Also, explicitly mention which test case would cover which equivalence class. (Hint: you must need to be ensure that the identified set of test cases cover all identified equivalence classes)**
Test cases:<br>
TC1: -1, 0 <br>
TC2: 1, 2, 5<br>
TC3: 3, 4, 5<br>
TC4: 5, 5, 7<br>
TC5: 6, 6, 6<br>
TC6: 3, 4, 5<br>

Test case 1 covers class 1, test case 2 covers class 2, test case 3 covers class 3, test case 4 covers class 4, test case 5 covers class 5, and test case 6 covers class 6

**c) For the boundary condition A + B > C case (scalene triangle), identify test cases to verify the boundary.**
2, 3, 6<br>
3, 4, 8<br>
Both test cases have two sides that are shorter than the third side, and should not form a triangle

<br>

**d) For the boundary condition A = C case (isosceles triangle), identify test cases to verify the boundary.**
1, 2, 1<br>
0, 2, 0<br>
5, 6, 5<br>
Both test cases have two sides that are equal, but only test case 2 should form an isosceles triangle, other input are invalid.
<br>

**e) For the boundary condition A = B = C case (equilateral triangle), identify test cases to verify the boundary.**
5, 5, 5<br>
0, 0, 0<br>
Both test cases have all sides equal, but only test case 1 should form an equilateral triangle, other input are invalid.

<br>

**f) For the boundary condition A2 + B2 = C2 case (right-angle triangle), identify test cases to verify the boundary.**
3, 4, 5
0, 0, 0
-3, -4, -5
Both test cases satisfy the Pythagorean theorem, but only test case 1 should form right-angled triangle, other input are invalid.
triangle

<br>

**g) For the non-triangle case, identify test cases to explore the boundary.**
Test cases for the non-triangle case:<br>
TC11 (EC3): A=2, B=2, C=4 (sum of A and B is less than C)<br>

<br>

**h) For non-positive input, identify test points.**
Test points for non-positive input:<br>
TP1 (EC2): A=0, B=4, C=5 (invalid input)<br>
TP2 (EC2): A=-2, B=4, C=5 (invalid input)<br>
Note: Test cases TC1 to TC10 covers all identified equivalence classes.<br>
<br>


# Section B:
1. Control Flow Graph (CFG):
```
        +-----+
        | i = 1|
        +-----+
           |
           |
           v
+---------------+
| i < p.size()   |
+---------------+
     | true
     |
     v
+-----------------------+
| ((Point)p.get(i)).y < ((Point)p.get(min)).y |
+-----------------------+
    | true        | false
    |             |
    v             v
+---------------+    +---------------+
| min = i       |    | i++           |
+---------------+    +---------------+
     |                   |
     |                   |
     v                   v
+---------------+    +---------------+
| i < p.size()   |    | return doStack(p) |
+---------------+    +---------------+
     | false             |
     |                   |
     v                   v
+------------------------+
| ((Point)p.get(i)).y == ((Point)p.get(min)).y |
+------------------------+
        | true           | false
        |                |
        v                v
+------------------------+  +---------------+
| ((Point)p.get(i)).x > ((Point)p.get(min)).x|
+------------------------+  +---------------+
        | true           | false
        |                |
        v                v
+---------------+    +---------------+
| min = i       |    | i++           |
+---------------+    +---------------+
        |                |
        |                |
        v                v
+---------------+    +---------------+
| i < p.size()   |    | return doStack(p) |
+---------------+    +---------------+
        | false            |
        |                  |
        v                  v
+--------------------------+
| return doStack(p)         |
+--------------------------+
```

**2. Test sets**<br>

Statement coverage test sets: To achieve statement coverage, we need to make sure that every statement in the code is executed at least once.<br>
Test 1: p = empty vector<br>
Test 2: p = vector with one point<br>
Test 3: p = vector with two points with the same y component<br>
Test 4: p = vector with two points with different y components<br>
Test 5: p = vector with three or more points with different y components<br>
Test 6: p = vector with three or more points with the same y component<br>


Branch coverage test sets: To achieve branch coverage, we need to make sure that every possible branch in the code is taken at least once<br>
Test 1: p = empty vector<br>
Test 2: p = vector with one point<br>
Test 3: p = vector with two points with the same y component<br>
Test 4: p = vector with two points with different y components<br>
Test 5: p = vector with three or more points with different y components, and none of them have the same x component<br>
Test 6: p = vector with three or more points with the same y component, and some of them have the same x component<br>
Test 7: p = vector with three or more points with the same y component, and all of them have the same x component<br>


Basic condition coverage test sets: To achieve basic condition coverage, we need to make sure that every basic condition in the code (i.e., every Boolean subexpression) is evaluated as both true and false at least once<br>
Test 1: p = empty vector<br>
Test 2: p = vector with one point<br>
Test 3: p = vector with two points with the same y component, and the first point has a smaller x component<br>
Test 4: p = vector with two points with the same y component, and the second point has a smaller x component<br>
Test 5: p = vector with two points with different y components<br>
Test 6: p = vector with three or more points with different y components, and none of them have the same x component<br>
Test 7: p = vector with three or more points with the same y component, and some of them have the same x component<br>
Test 8: p = vector with three or more points with the same y component, and all of them have the same x component.<br>


# Here is the doc link containing eclipse JUnit Testing code results : <br>
https://docs.google.com/document/d/1usjPFBEwySX1td2iH29NkGVR15XwY3gDrmTdb6_uVL4/edit?usp=sharing
