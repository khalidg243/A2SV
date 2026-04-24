class Solution:
    def findRightInterval(self, intervals: List[List[int]]) -> List[int]:
        starts = []
        ans = []

        for i in range(len(intervals)):
            starts.append([intervals[i][0], i])
        
        starts.sort()

        for start , end in intervals:
            l , r = 0 , len(starts) - 1
            idx = -1

            while l <= r:
                mid = l + ((r-l) // 2)

                if starts[mid][0] >= end:
                    idx = starts[mid][1]
                    r = mid - 1
                else:
                    l = mid + 1

            ans.append(idx) 
        
        return ans
