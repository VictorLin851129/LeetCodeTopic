# 68. Text Justification
```
class Solution {
    public List<String> fullJustify(String[] words, int maxWidth) {
        List<String> retval = new ArrayList<String>();
        
        int[] StringCount = new int[words.length];
        GetStringCount(StringCount, words);
        
        int index = 0;
        while(index < words.length) {
        	StringBuilder str = new StringBuilder();
        	int MaxWordCount = maxWordCount(StringCount, index, maxWidth);
        	if(index + MaxWordCount == words.length) {	//last list
        		int LastBlankCount = 0;
        		for(int i = index; i < index + MaxWordCount; i++) {
        			str.append(words[i]);
        			if(i + 1 != words.length) {
        				str.append(" ");
        				LastBlankCount++;
        			}
        		}
        		
        		int TotalChar = GetTotalChar(index, MaxWordCount, StringCount);
        		int TotalBlank = GetTotalBlank(TotalChar, maxWidth);
        		for(int i = 0; i < TotalBlank - LastBlankCount; i++) {
        			str.append(" ");
        		}
        		
        	}else if(MaxWordCount == 1){
        		str.append(words[index]);
        		int TotalChar = GetTotalChar(index, MaxWordCount, StringCount);
        		int TotalBlank = GetTotalBlank(TotalChar, maxWidth);
        		for(int i = 0; i < TotalBlank; i++) {
        			str.append(" ");
        		}
        	}else {
        		int TotalChar = GetTotalChar(index, MaxWordCount, StringCount);
        		int TotalBlank = GetTotalBlank(TotalChar, maxWidth);
        		
        		for(int i = index; i < MaxWordCount + index; i++) {
        			str.append(words[i]);
        			for(int j = 0; !(i + 1 == MaxWordCount + index) && (j < TotalBlank / (MaxWordCount - 1)); j++) {
        				str.append(" ");
        			}
        			if(TotalBlank % (MaxWordCount - 1) > 0) {
        				str.append(" ");
        				TotalBlank--;
        			}
        		}
        	}
        	index += MaxWordCount;
        	retval.add(str.toString());
        }
        
        return retval;
    }
    
    public static void GetStringCount(int[] StringCount, String[] words) {
    	int index = 0;
    	for(String s : words) {
    		StringCount[index++] = s.length();
    	}
    }
    
    public static int maxWordCount(int[] StringCount, int index, int maxWidth) {
    	int retval = 1;
    	int totalChar = StringCount[index];
    	
    	for(int i = index + 1; i  < StringCount.length; i++) {
    		if(totalChar + StringCount[i] + retval > maxWidth) {//minus blank place
    			break;
    		}
    		totalChar += StringCount[i];
    		retval++;
    	}
    	
    	return retval;
    }
    
    public static int GetTotalChar(int index, int MaxWordCount, int[] StringCount) {
    	int retval = 0;
    	
    	for(int i = index; i < index + MaxWordCount; i++) {
    		retval += StringCount[i];
    	}
    	
    	return retval;
    }
    
    public static int GetTotalBlank(int TotalChar, int maxWidth) {
    	return maxWidth - TotalChar;
    }
}
```
### Time complexity: O(n * m / k)
#### Where n islength of words
#### Where m is length of maxWidth
#### Where k is length of average word length
### Space complexity: O(m / k)
#### Where m is length of maxWidth
#### Where k is length of average word length