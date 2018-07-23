
Given a non-overlapping interval list which is sorted by start point.

Insert a new interval into it, make sure the list is still in order and non-overlapping (merge intervals if necessary).

Example
Insert (2, 5) into [(1,2), (5,9)], we get [(1,9)].

Insert (3, 4) into [(1,2), (5,9)], we get [(1,2), (3,4), (5,9)].

    /**
     * Definition of Interval:
     * public classs Interval {
     *     int start, end;
     *     Interval(int start, int end) {
     *         this.start = start;
     *         this.end = end;
     *     }
     * }
     */

    public class Solution {
        /**
         * @param intervals: Sorted interval list.
         * @param newInterval: new interval.
         * @return: A new interval list.
         */
        public List<Interval> insert(List<Interval> intervals, Interval newInterval) {
            // write your code here
            List<Interval> ans = new ArrayList<>();
            int index = 0;
            while (index < intervals.size() && intervals.get(index).start < newInterval.start) {
                index++;
            }
            intervals.add(index, newInterval);
            Interval last = null;
            for (Interval item: intervals) {
                if (last == null || last.end < item.start) {
                    ans.add(item);
                    last = item;
                }
                else {
                    last.end = Math.max(last.end, item.end);
                }
            }
            return ans;
        }
    }
