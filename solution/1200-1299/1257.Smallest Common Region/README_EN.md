# [1257. Smallest Common Region](https://leetcode.com/problems/smallest-common-region)

[中文文档](/solution/1200-1299/1257.Smallest%20Common%20Region/README.md)

## Description

<p>You are given some lists of <code>regions</code>&nbsp;where the first region of each list includes all other regions in that list.</p>

<p>Naturally, if a region <code>X</code>&nbsp;contains another region <code>Y</code>&nbsp;then <code>X</code>&nbsp;is bigger than <code>Y</code>. Also by definition a region X contains itself.</p>

<p>Given two regions <code>region1</code>, <code>region2</code>, find out the <strong>smallest</strong> region that contains both of them.</p>

<p>If you are given regions <code>r1</code>, <code>r2</code> and <code>r3</code> such that <code>r1</code> includes <code>r3</code>, it is guaranteed there is no <code>r2</code> such that <code>r2</code> includes <code>r3</code>.<br />
<br />
It&#39;s guaranteed the smallest region exists.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:
</strong>regions = [[&quot;Earth&quot;,&quot;North America&quot;,&quot;South America&quot;],
[&quot;North America&quot;,&quot;United States&quot;,&quot;Canada&quot;],
[&quot;United States&quot;,&quot;New York&quot;,&quot;Boston&quot;],
[&quot;Canada&quot;,&quot;Ontario&quot;,&quot;Quebec&quot;],
[&quot;South America&quot;,&quot;Brazil&quot;]],
region1 = &quot;Quebec&quot;,
region2 = &quot;New York&quot;
<strong>Output:</strong> &quot;North America&quot;
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= regions.length &lt;= 10^4</code></li>
	<li><code>region1 != region2</code></li>
	<li>All strings consist of English letters and spaces with at most 20 letters.</li>
</ul>

## Solutions

<!-- tabs:start -->

### **Python3**

```python
class Solution:
    def findSmallestRegion(self, regions: List[List[str]], region1: str, region2: str) -> str:
        m = {}
        for region in regions:
            for r in region[1:]:
                m[r] = region[0]
        s = set()
        while m.get(region1):
            s.add(region1)
            region1 = m[region1]
        while m.get(region2):
            if region2 in s:
                return region2
            region2 = m[region2]
        return region1
```

### **Java**

```java
class Solution {
    public String findSmallestRegion(List<List<String>> regions, String region1, String region2) {
        Map<String, String> m = new HashMap<>();
        for (List<String> region : regions) {
            for (int i = 1; i < region.size(); ++i) {
                m.put(region.get(i), region.get(0));
            }
        }
        Set<String> s = new HashSet<>();
        while (m.containsKey(region1)) {
            s.add(region1);
            region1 = m.get(region1);
        }
        while (m.containsKey(region2)) {
            if (s.contains(region2)) {
                return region2;
            }
            region2 = m.get(region2);
        }
        return region1;
    }
}
```

### **C++**

```cpp
class Solution {
public:
    string findSmallestRegion(vector<vector<string>>& regions, string region1, string region2) {
        unordered_map<string, string> m;
        for (auto& region : regions)
            for (int i = 1; i < region.size(); ++i)
                m[region[i]] = region[0];
        unordered_set<string> s;
        while (m.count(region1))
        {
            s.insert(region1);
            region1 = m[region1];
        }
        while (m.count(region2))
        {
            if (s.count(region2)) return region2;
            region2 = m[region2];
        }
        return region1;
    }
};
```

### **...**

```

```

<!-- tabs:end -->
