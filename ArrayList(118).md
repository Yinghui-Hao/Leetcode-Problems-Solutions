###118. [Pascal's Triangle](https://leetcode.com/problems/pascals-triangle/#/description) 
>Given numRows, generate the first numRows of Pascal's triangle.  

>For example, given numRows = 5,  
>Return   
```
[
     [1],
    [1,1],
   [1,2,1],
  [1,3,3,1],
 [1,4,6,4,1]
]
```
----
### Java
```
public class Solution {
    public List<List<Integer>> generate(int numRows) {
        List<List<Integer>> allrows = new ArrayList<List<Integer>>();
        ArrayList<Integer>  row = new ArrayList<Integer>();
        for(int i = 0; i < numRows; i++){
            row.add(0,1);
            for(int j = 1; j < i; j++ ){
                row.set(j,row.get(j)+row.get(j+1));
            }
            allrows.add(new ArrayList<Integer>(row));
        }
        return allrows;
    }
}
//List中的set方法和add方法: http://blog.csdn.net/alibert/article/details/2855475
/*
public class Solution {
	public List<List<Integer>> generate(int numRows) {
		List<List<Integer>> res = new ArrayList<List<Integer>>();
		List<Integer> row, pre = null;
		for (int i = 0; i < numRows; ++i) {
			row = new ArrayList<Integer>();
			for (int j = 0; j <= i; ++j)
				if (j == 0 || j == i)
					row.add(1);
				else
					row.add(pre.get(j - 1) + pre.get(j));
			pre = row;
			res.add(row);
		}
		return res;
	}
}
*/
```
