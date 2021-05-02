# 12. Integer to Roman
# enum
```
class Solution {
    enum Chart{
		M	(1000),
		CM	(900),
		D	(500),
		CD	(400),
		C	(100),
		XC	(90),
		L	(50),
		XL	(40),
		X	(10),
		IX	(9),
		V	(5),
		IV	(4),
		I	(1);
		
		private final int val;
		
		Chart(int val) {
			this.val = val;
		}
	}
    public String intToRoman(int num) {
        StringBuilder ans = new StringBuilder();
        
        for(Chart chart : Chart.values()) {
        	while(chart.val <= num) {
        		num -= chart.val;
        		ans.append(chart);
        	}
        }
       
        return ans.toString();
    }
}
```
### Time complexity: O(n)
#### Where n is length of num
### Space complexity: O(n)
#### Where n is length of num