#AI based ddos setection and mitigation 
pipeline : traffic --> Feature extraction -> AI classifier -> Mitigation 
##Interface (do not change it without others knowing 
1. Features : names and order are defined in model/features.json 
2. Data : CSV with exactly those columns, in that order, plus a 'label' column (0/1) for training data 
3. Model: loaded with joblib.load ("model/model.pkl"); predict() returns 0(normal) or 1 (attack)

## Feature units 
- flow_duration: seconds 
-packets_per_sec: packets/s
- bytes_per_sec: bytes/s
- avg_packet_size: bytes 
- src_ip_entropy: bits
- protocol : 6 = TCP, 17 = UDP, 1 = TCMP 

##STRUCTURE 
- data/, model/ : person1 (dataset, training, model.pkl)
- network/: person 2 (Mininet topology, attack and normal traffic, captures)
- engine/: person 3 (detector.py, mitigation.py, dashboard)
- docs/: report and diagrams 

## working rules 
- one branch per person, merged into main when something works 
- any change to features.json must be announced to the whole team 
