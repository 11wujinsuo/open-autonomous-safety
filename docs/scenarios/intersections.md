# Intersections

:::warning Alpha
Work In Progress
:::

[[toc]]

## Configurations
There are many combinations of intersection scenarios.

 - ego starting location: `[west] //ego always starts on the west`
 - ego direction: `[straight, left, right]`
 - roadway type: `[3-way, 4-way, other road configurations]`
 - stopping pattern: `[1-way (north/south/east/west), 2-way (north/south/east/west), 3-way (north/south/east/west), 4-way (north/south/east/west), other]`
 - secondary vehicle(s): `[none, bus, car, golf cart, motorcycle, bicycle]`
 - secondary vehicle(s) starting position: `[n/a, north, east, south, west]`
 - secondary vehicle(s) ending position: `[n/a, north, east, south, west]`
 - right of way: `[n/a, secondary has right of way, Ego has right of way, Ego has right of way but secondary takes it (misbehaves), more vehicles or more complex scenarios]`

The following are examples on how these various configurations can be put together and modeled, with the expectation that all combinations will be detailed as this project continues.

## 4-Way controlled intersection with no other vehicles
**4-2-NESW-I-STR-XX**

|      |     |     |
| :--: | --- | --- |
| A    | ![I-01-A](./images/I-01-A.png) | **Scenario** <br> Ego approaches the intersection. There are no other vehicles. <br><br> **Expected Result** <br> Ego comes to a stop in front of the stopline. |
| B    | ![I-01-B](./images/I-01-B.png) | **Scenario** <br> *n/a* <br><br> **Expected Result** <br> Ego proceeds through the intersection. |
| C    | ![I-01-C](./images/I-01-C.png) | **Scenario Complete 🎉** |


## 3-Way controlled intersection with another vehicle
**3-2-ESW-I-STR-CAR:S>W:02**

|      |     |     |
| :--: | --- | --- |
| A    | ![I-02-A](./images/I-02-A.png) | **Scenario** <br> Ego approaches the intersection. Secondary vehicle approaches from South and stops. <br><br> **Expected Result** <br> Ego comes to a stop in front of the stopline. |
| B    | ![I-02-B](./images/I-02-B.png) | **Scenario** <br> Secondary vehicle turns left <br><br> **Expected Result** <br> Ego remains stopped. |
| C    | ![I-02-C](./images/I-02-C.png) | **Scenario** <br> Secondary vehicle clears the intersection. <br><br> **Expected Result** <br> Ego proceeds through the intersection. |
| D    | ![I-02-D](./images/I-02-D.png) | **Scenario Complete 🎉** |

**3-2-NSW-I-L-CAR:S>W:02**

|      |     |     |
| :--: | --- | --- |
| A    | ![I-05-A](./images/I-05-A.png) | **Scenario** <br> Ego approaches the intersection. Secondary vehicle approaches from South and stops first. <br><br> **Expected Result** <br> Ego comes to a stop in front of the stopline. |
| B    | ![I-05-B](./images/I-05-B.png) | **Scenario** <br> Secondary vehicle turns left <br><br> **Expected Result** <br> Ego remains stopped. |
| C    | ![I-05-C](./images/I-05-C.png) | **Scenario** <br> Secondary vehicle clears the intersection. <br><br> **Expected Result** <br> Ego proceeds through the intersection. |
| D    | ![I-05-D](./images/I-05-D.png) | **Scenario Complete 🎉** |

**3-2-NSW-I-L-CAR:S>W:01**

|      |     |     |
| :--: | --- | --- |
| A    | ![I-06-A](./images/I-06-A.png) | **Scenario** <br> Ego stops at the intersection. Secondary vehicle approaches from South but hasn't reached stop line yet. <br><br> **Expected Result** <br> Ego begins to proceed through the intersection. |
| B    | ![I-06-B](./images/I-06-B.png) | **Scenario** <br> Secondary vehicle waits at the stop line. <br><br> **Expected Result** <br> Ego continues through intersection. |
| C    | ![I-06-C](./images/I-06-C.png) | **Scenario Complete 🎉** |

**3-2-NSW-I-L-CAR:S>N:03**

|      |     |     |
| :--: | --- | --- |
| A    | ![I-07-A](./images/I-07-A.png) | **Scenario** <br> Ego stops at the intersection. Secondary vehicle approaches from South but hasn't reached stop line yet. <br><br> **Expected Result** <br> Ego begins to proceed through the intersection. |
| B    | ![I-07-B](./images/I-07-B.png) | **Scenario** <br> Secondary vehicle does not stop and starts to proceed through intersection. <br><br> **Expected Result** <br> Ego stops to yield to misbehaving secondary vehicle. |
| C    | ![I-07-C](./images/I-07-C.png) | **Scenario** <br> Secondary vehicle continues through intersection. <br><br> **Expected Result** <br> Ego remains stopped until secondary vehicle is out of intersection and then proceeds. |
| D    | ![I-07-D](./images/I-07-D.png) | **Scenario Complete 🎉** |


## 3-Way uncontrolled intersection with another vehicle
**3-2-W-I-L-CAR:N>S**

|      |     |     |
| :--: | --- | --- |
| A    | ![I-03-A](./images/I-03-A.png) | **Scenario** <br> Ego approaches intersection. Secondary vehicle approaches from North and enters the intersection. <br><br> **Expected Result** <br> Ego comes to a stop in front of the stopline. |
| B    | ![I-03-B](./images/I-03-B.png) | **Scenario** <br> Secondary vehicle continues through the intersection. <br><br> **Expected Result** <br> Ego remains stopped. |
| C    | ![I-03-C](./images/I-03-C.png) | **Scenario** <br> Secondary vehicle clears the intersection. <br><br> **Expected Result** <br> Ego proceeds through the intersection (turns left). |
| D    | ![I-03-D](./images/I-03-D.png) | **Scenario Complete 🎉** |

**3-2-S-I-STR-CAR:S>W**

|      |     |     |
| :--: | --- | --- |
| A    | ![I-04-A](./images/I-04-A.png) | **Scenario** <br> Ego approaches intersection and it is clear. Secondary vehicle approaches from South and stops at intersection. <br><br> **Expected Result** <br> Ego proceeds through the intersection. |
| B    | ![I-04-B](./images/I-04-B.png) | **Scenario Complete 🎉** |

**3-2-S-I-STR-CAR:S>W:04**

|      |     |     |
| :--: | --- | --- |
| A    | ![I-08-A](./images/I-08-A.png) | **Scenario** <br> Ego approaches intersection and secondary vehicle is occupying intersection. <br><br> **Expected Result** <br> Ego stops for secondary vehicle and waits until intersection is clear. |
| B    | ![I-08-B](./images/I-08-B.png) | **Scenario** <br> Secondary vehicle clears intersection. <br><br> **Expected Result** <br> Ego proceeds through intersection. |
| B    | ![I-08-C](./images/I-08-C.png) | **Scenario Complete 🎉** |
