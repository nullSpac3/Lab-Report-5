## Part 1

**What environment are you using (computer, operating system, web browser, terminal/editor, and so on)?**

* **Computer**: Asus ROG
* **Operating System**: Windows
* **Web Browser**: Google Chrome
* **Code Editor**: VScode

**Detail the symptom you're seeing. Be specific; include both what you're seeing and what you expected to see instead. Screenshots are great, copy-pasted terminal output is also great. Avoid saying "it doesn't work".**

The symptom presented below shows that the output is the second to last element when the array is supposedly sorted in ascending order. The code respective to the symptom is. The expected output is detailed by the `assertEquals()` method.

```
public class BubbleSort{
    public static void bubbleSort(int arr[]){
        for (int i = 0; i < arr.length; ++i){
            for (int j = 0; j < arr.length - i - 2; ++j) {
                if (arr[j] > arr[j + 1]){
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                }
            }
        }
        
    }
}
```
**Bash Script (script.sh)**
```
javac -cp ".;lib/hamcrest-core-1.3.jar;lib/junit-4.13.2.jar" *.java
java -cp ".;lib/junit-4.13.2.jar;lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore BoundErrorS
```

![Image](run.png)

<br>

**Detail the failure-inducing input and context. That might any or all of the commands you're running, a test case, command-line arguments, working directory, even the last few commands you ran. Do your best to provide as much context as you can.**


The failure inducing input would be the expectation that the greatest element of the sorted array would be 5, that is, `assertEquals(5, arr.length() - 1)`. I am attempting to run my own rendition of the bubble sort algorithm but it seems to not have taken into account the greatest element of the array, in this case, `5`.


<br>

**TA Response**

Looking at the bubbleSort code, it seems to not take into account the last element of the array when comparing and swapping values. I would suggest revising the inner for loop's definition.

<br>

**Fixed Code**


Turns out the reason the greatest element was neglected was because my for loop condition did not iterate through and compare all values. I simply had to replace `arr.length - i - 2` with `arr.length - i - 1`.
```
public class BubbleSort{
    public static void bubbleSort(int arr[]){
        for (int i = 0; i < arr.length; ++i){
            for (int j = 0; j < arr.length - i - 1; ++j) {
                if (arr[j] > arr[j + 1]){
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                }
            }
        }
        
    }
}
```


## Part 2 - Reflection 

I found vim quite interesting, despite it being difficult to work with at first. It feels like a shortcut for programming and something I should utilize more. The ability to quickly edit and sace files for example is quite satisfying. More generally however, I like that I am more familiar with working with terminals and hope to utilize it more in the future.

