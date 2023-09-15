# Managing Scheduling

(Anti-)Affinity is used to define advanced scheduler rules

Node Affinity is used to constrain a node that can receive a Pod by matching labels of these nodes

Inter-pod affinity constrains nodes to receive Pods by matching labels of existing Pods already running on that node. In other words:

“*A pod that has a pod affinity label of key=value will only be schedule to nodes running Pods Pods with the matching label”*

Anti-affinity can only be applied between pods 

In Kubernetes, both Node Affinity and Pod Affinity/Anti-Affinity are mechanisms for influencing the scheduling of pods onto nodes based on specific conditions and constraints.

### **Node Affinity:**

**Node Affinity** is used to define rules that influence pod scheduling based on node characteristics, such as node labels. Node Affinity can be further categorized into **required** and **preferred**.

- **Required Node Affinity**: Pods with required node affinity rules must be scheduled on nodes that match the specified conditions. If no nodes match the conditions, the pod remains unscheduled.
- **Preferred Node Affinity**: Pods with preferred node affinity rules prefer to be scheduled on nodes that match the specified conditions, but they are not required to. If no nodes match the conditions, the pod can still be scheduled on other nodes.


### **Pod Affinity and Anti-Affinity:**

**Pod Affinity** and **Pod Anti-Affinity** are used to define rules that influence pod scheduling based on the presence or absence of other pods on the same node.

- **Pod Affinity**: Specifies rules for preferring pods to be scheduled on nodes that have certain pods already running.
- **Pod Anti-Affinity**: Specifies rules for avoiding scheduling pods on nodes that have certain pods already running.


These affinity and anti-affinity rules allow you to control pod placement based on factors like high availability, co-location of related services, or segregation of certain workloads.