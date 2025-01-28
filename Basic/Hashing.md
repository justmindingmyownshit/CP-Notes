# Hashing


### Why Hashing ?
Lets take a example

To count the **numbers which are repeated in an array**, we use a traditional method.

```c++
void repeat(int number){
    int cnt = 0;
    array<int, 5> arr = {1, 3, 1, 5, 2};
    for(int i = 0; i < arr.size(); i++){
        if(arr[i] == number) cnt++;
    }    
    cout << "The number is repeated :" << cnt;
}

int main(){
    repeat(1);
}
```


> If the number of input is increased to search the array the **time complexity increases**.

If the **input is 5** to search
The Time Complexity is **( 5 x O(n) )**

---

# With Hashing

### - Pre Compute / Fetching

With hashing a **create a array with the value of 0**.
We iterate over the array and in the index of the array we **increment it to one**.

> Lets see a example

```c++
int main(){
    int  n;
    cin >> n;
    int arr[n];
    for( int i = 0; i < n; i++){
        cin >> arr[i];
    }
    
    //pre compute
    int hash[6] = {0};
    for(int i = 0; i < n; i++){
        hash[arr[i]]++;
    }
    
    int q;
    cin >> q;
    while(q--){
        int number;
        cin >> number;
        
        // fetch 
        cout << hash[number] << endl;
    }
}
```
> Input for number is

| 1 | 3 | 1 | 5 | 2 |
| - | - | - | - | - |

> **The value in the hash Would be**

| 0 | 2 | 1 | 1 | 0 | 1 | 0 | 
| - | - | - | - | - | - | - |
| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 

The **Output** Will be 

1 => 2

2 => 1

3 => 1

4 => 0

5 => 1


> In this code
```c++
hash[arr[i]]++;
```

It states that, If **i = 0**, then **arr[i] = 1**.

Then **hash[arr[i]]** is **hash[1]**. The index of **1** in **the array hash is 2**.

*And the output is **2** as it is repeated.*

## With char :

```c++
    string s;
    cin >> s;

    // pre compute
    int hash[256] = {0};
    for(int i = 0; i < s.size(); i++){
        hash[s[i]]++;
    }

    int q;
    cin >> q;

    while(q--){
        char c;
        cout << endl;
        cin >> c;

        // Fetch
        cout << hash[c] << endl;
    }
```

The character has a ASCII Value and the values are identified by the machine and are stored in the array with the respective position in the hash.

---

# Hashing With Map

> **In hashing we use array and declare ( n ) numbers in it.** and we iterate over the array, for each input **we increment the value in the index of the hash**.

In this the array gets a fixed size even if we use very less input for example, **arr [1, 4, 6, 12]** in this, the of the **array has the size of arr[ 13 ]** and takes more space. And in main function the max size in a array is **[ 10^6 ]**

**Instead we use a efficient method, in C++ STL there is something called map**. in map only the input numbers are inserted and iterated. Which is more efficient and uses very less space than array.

> **Is there anything I want to see More than this in hashing ??**
Sorry Man I don't know !!

```C++
    int n;
    cin >> n;
    int arr[n];
    for( int i = 0; i < n; i++){
        cin >> arr[i];
    }

    map<int, int> mpp;
    for( int i = 0; i < n; i++){
        mpp[arr[i]]++;
    }

    for(auto it : mpp){
        cout << it.first << "=>" << it.second;
    }

    int q;
    cin >> q;
    while(q--){
        int number;
        cout << endl;
        cin >> number;

        // Fetch
        cout << mpp[number] << endl;
    }
```

The input would be 

| 1 | 2 | 3 | 1 | 3 | 2 | 12 |
| - | - | - | - | - | - | - |

**In the Stack Space, It holds**

| Key | Value |
| - | - |
| 12 | 1 |
| 3 | 2 |
| 2 | 2 |
| 1 | 2 |

It hold only the values that are in the input, With the help of **Map**, *rather than holding the ( n ) size of array*.
