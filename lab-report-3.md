# Lab Report 3
## Part 1
This is the original code for the method `reverseInPlace`.
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```
Below is the JUnit test for a failure inducing input.
```
@Test
  public void testReverseInPlace1(){
    int[] input1 = {1,2,3};
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{3,2,1}, input1);
  }
```
Below is the JUnit test for an input that doesn't produce a failure.
```
@Test 
	public void testReverseInPlaceSingle() {
    int[] input1 = {3};
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{3}, input1);
	}
```
Here is the output of running the two tests mentioned.
![Image](CSE15L-Lab3-Q1.png)


Here is the fixed code that addresses the bug.
```
static void reverseInPlace(int[] arr) {
    int previous  = arr[0];
    for(int i = 0; i < arr.length/2; i += 1) {
      arr[i] = arr[arr.length - 1 -i];
      arr[arr.length -1 -i] = previous;
      previous = arr[i+1];
    }
  }
```
The 

## Part 2
