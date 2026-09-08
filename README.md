# The-Auction-House-s-Running-Bid-Rank

An auction house is tracking bids for a rare painting. There is an integer k the auctioneer cares about, and an initial list of initN bids already placed before the auctioneer started watching closely (with initN \geq k). After that, m more bids arrive one at a time, live.

Each time a new bid arrives, the auctioneer wants to announce the k-th highest bid placed so far among all bids seen (counting equal bid amounts separately, not as one distinct value).

Input The first line contains two integers k k and i n i t N initN — the rank to announce and the number of bids already placed. The second line contains i n i t N initN integers, the already-placed bid amounts. The third line contains a single integer m m — the number of live bids that follow. The fourth line contains m m integers, the live bid amounts, in the order they arrive.

Output Print m m integers, space-separated — the k k-th highest bid announced immediately after each live bid arrives, in order.

import heapq

k, initN = map(int, input().split())
initial = list(map(int, input().split()))

# Min-heap containing the k largest bids
heap = []

for x in initial:
    heapq.heappush(heap, x)
    if len(heap) > k:
        heapq.heappop(heap)

m = int(input())
live_bids = list(map(int, input().split()))

answer = []

for x in live_bids:
    if x > heap[0]:
        heapq.heapreplace(heap, x)

    answer.append(heap[0])

print(*answer)
