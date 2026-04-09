# Experimental Data Description

This folder contains the input data and generated experimental instances used in the computational experiments.

---

## 1. Folder Structure

The main files and folders include:

- `parameters.txt`
- `locker_info.csv`
- `shenzhen_shopping_centers(candidate_drone_launching_stations).xlsx`
- `instance_data_drone_delivery.zip`

The file `instance_data_drone_delivery.zip` contains all 60 experimental instances used in the study.

It includes instance files such as:

- `A_10_1.xlsx`, `A_10_2.xlsx`, ..., `A_10_10.xlsx`
- `A_20_1.xlsx`, `A_20_2.xlsx`, ..., etc.

Each file corresponds to one specific instance. For example, `A_10_1.xlsx` denotes the first instance in the group containing 10 orders.

---

## 2. File and Folder Descriptions

### 2.1 `parameters.txt`

This file contains the parameter settings used in the computational experiments. These parameters are used to calculate the values of the model parameters introduced in Section 3.2 of the manuscript.

It contains:
- `|K| = 50`: number of drones
- `drone_speed = 36 km/h`
- `courier_travel_speed = 20 km/h`

---

### 2.2 `locker_info.csv`

This file contains the parcel locker data used in all instances.

#### Columns
- `locker_ID`: unique locker ID
- `locker_name`: locker name
- `lng`: longitude
- `lat`: latitude

#### Notes
- The locker set remains the same across all instances, because this file contains all 1,051 lockers obtained in Section 5.2.
- Locker locations are based on real geographic data.
---

### 2.3 `shenzhen_shopping_centers(candidate_drone_launching_stations).xlsx`

This file contains the candidate shopping centers used as potential drone launching stations.

#### Columns
- `shopping_center_name`: shopping center name
- `lng`: longitude
- `lat`: latitude

#### Notes
- These shopping centers form the candidate station pool.
- The station set in each instance is selected from this file.

---

### 2.4 `instance_data_drone_delivery.zip`

This file contains all 60 experimental instances used in this study.

Each experimental instance is stored as an `.xlsx` file. Each file contains two sheets:

1. `drone_launching_stations`: this sheet records the drone launching stations selected in that instance.
2. `orders`: this sheet records the generated customer orders in that instance.

Typical files include:
- `A_10_1.xlsx`
- `A_10_2.xlsx`
- ...
- `A_20_1.xlsx`
- `A_20_2.xlsx`

For example, `A_10_1.xlsx` denotes the first instance in the group containing 10 orders.

---

## 3. Instance File Format

Each instance file in `instance_data_drone_delivery.zip` is stored in `.xlsx` format and contains two sheets: `drone_launching_stations` and `orders`.

### 3.1 Sheet `drone_launching_stations`

This sheet records the drone launching stations selected in that instance.

#### Columns
- `station_ID`: unique station ID
- `station_name`: station name
- `lng`: longitude
- `lat`: latitude

### 3.2 Sheet `orders`

This sheet records the generated customer orders in that instance.

#### Columns
- `order_ID`: unique order ID
- `org_lng`: longitude of the order origin
- `org_lat`: latitude of the order origin
- `des_lng`: longitude of the order destination
- `des_lat`: latitude of the order destination
- `start_time_in_minute`: order start time in minutes

---

## 4. Naming Rule of Instance Files

The instance files follow the naming format:

`A_x_y.xlsx`

where:

- `x`: number of orders in the instance
- `y`: instance index under the same order size

For example:

- `A_10_1.xlsx`: the 1st instance with 10 orders
- `A_10_8.xlsx`: the 8th instance with 10 orders
- `A_20_1.xlsx`: the 1st instance with 20 orders

Therefore, files with the same first number belong to the same size group, while the second number distinguishes different randomly generated instances.

---

## 5. Example: `A_10_1.xlsx`

This file is one generated instance in `instance_data_drone_delivery.zip`.

It contains:
- a station set;
- an order set.

### Example station records
| station_ID | station_name        | lng        | lat       |
|------------|---------------------|------------|-----------|
| 0          | shopping_center_69  | 114.046937 | 22.647722 |
| 1          | shopping_center_399 | 114.048166 | 22.641233 |
| 2          | shopping_center_194 | 114.109687 | 22.549125 |

### Example order records
| order_ID | org_lng       | org_lat       | des_lng       | des_lat       | start_time_in_minute |
|----------|---------------|---------------|---------------|---------------|----------------------|
| 0        | 114.043280642 | 22.644065642  | 114.027541984 | 22.628326984  | 668                  |
| 1        | 114.110067121 | 22.549505121  | 114.131882482 | 22.571320482  | 694                  |
| 2        | 114.047037391 | 22.640104391  | 114.030108248 | 22.623175248  | 684                  |
......
......

---

## 7. Notes

1. Longitude and latitude are given in geographic coordinates.
2. Geographic distances should be computed using an appropriate distance formula when needed.
3. The locker dataset is remain the same for all instances.
4. Station sets and order sets vary across different instance files.

