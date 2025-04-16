## Projects 

### Buffer Management Tracker
Problem Statement: No single source of truth for buffer levels throughout Tesla Megafactory. 

**Actions:** 
1. Identified which stations produced items that were critical buffers to their respective lines- buffers observed by production associates and leads to be frequently low, or stations whose machines failed frequently.
2. Documented units in which we talked about each buffer- e.g. 1 tray of fans, 1 cart of doors, 1 enclosure. 
3. Calculated the safe minimum buffer quantity for each station. I did this in an ad-hoc way, but since then I've learned about Economic Order Quantity. As such I would revise my approach, to calculate the reorder point r = λL, where L is the lead time for that buffer item and λ is the demand. For example, say I wanted to flag when the buffer coming from the manifold subassembly (let's call that Station A) was low. I would calculate the time it takes for 10 manifolds to be transported from the subassembly station to the station "B" that consumes the manifolds - that's L. Then I would calculate how many manifolds are consumed by Station B per hour- that's λ. Making sure the units of L and λ are the same (e.g., L = 4 min = 1/15 hr, and λ = 30 doors/hr), I can calculate r = 30 manifolds/hr * (1/15 hr) = 2 manifolds. Therefore, I would only flag that I needed more manifolds at Station B, from Station A, when I hit 2 manifolds in inventory. Of course, this assumes that only 1 manifold is needed per cycle at Station B. Also, it might be better if the manifolds were more continuously supplied to Station B for a variety of reasons such as worker optimization.
4. Finally, armed with my understanding of the factory layout and optimal buffer reorder points, I created a dashboard in Excel that displayed buffer & WIP (work in progress) counts for all stations in the factory. This dashboard was updated daily by real people from the Operations Control Center team, as well as by MOS Power Queries where possible. When the WIP or buffer counts in any station was lower than the accepted minimum, the respective cell was highlighted red to indicate a problem. 

**Results:** The dashboard is a source of truth used daily by management as an immediate identification of critically low buffers. Using it helps mitigate downtime due to inventory stockout and station starvation. 
