1. failure- including input for the Program
* For ReverseInPlace method:
Test Code:
```
  @Test 
	public void testReverseInPlace2() {
    int[] input1 = { 1,2,3,4,5,6,7,8 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 8,7,6,5,4,3,2,1 }, input1);
	}

```
Associated code:
```
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```
2. Input that doesn't induce a failure
   Test Code:
```
	@Test 
	public void testReverseInPlace() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
	}
```
Associated code:
```
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```
3.Symptom
![image](https://github.com/ziyexiaohei/cse15l-lab-reports/assets/146874199/d18383cf-a038-4a3f-b8dc-71b37c9700cc)


4.Fix
Before:
```
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```

After:
```
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length/2; i += 1) {
      int temp= arr[i];
      arr[i] = arr[arr.length - i - 1];
      arr[arr.length - i -1] = temp
    }
  }
```
Explaination: In the code before we fix, it will only reverse half of of the array, for example {1,2,3,4,5,6,7,8}, the code will replace the first 4 element of the arrray with the last 4 element, which make the array into {8,7,6,5,5,6,7,8} in the fourth element we want to have is 4, but according to the code it will be 5, because, after we updated the array the fourth element will be replace by the third element, in the new array fourth element and fifth element is the same, thus error occur.
<br>
Solution: The solution to this bug is that we can just swap the relative element, we store the element of array we going to replace into temp, in our example we want to replace element[0] with element[7], we store element[0] into temp, replace it with element[7], then put the value store in temp into element[7]. By doing this we can keep track of every element, and we only need to iterate half of the array, and the problem will be solved, since we not only updated the first half element of the array, and also we updated the last half of array.
