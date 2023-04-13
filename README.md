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
TestCases for Program 1: 
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

 

