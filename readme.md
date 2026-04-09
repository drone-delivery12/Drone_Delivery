# Experimental Data Description

This folder contains the input data and generated experimental instances used in the computational experiments.

---

## 1. Folder Structure

The main files and folders include:

- `parameters.txt`
- `locker_info.csv`
- `shenzhen_shopping_centers(candidate_drone_launching_stations).xlsx`
- `order_instance_group_999/`

The folder `order_instance_group_999` stores a batch of generated order instance files, such as:

- `A_10_1.xlsx`, `A_10_2.xlsx`, ..., `A_10_10.xlsx`
- `A_20_1.xlsx`, `A_20_2.xlsx`, ..., etc.

Files such as `A_10_1.xlsx` are batch-generated instance files.

---

## 2. File and Folder Descriptions

### 2.1 `parameters(1).txt`

This file records the main experimental parameters.

Example contents:
- `|K| = 50`: number of drones
- `drone_speed = 36 km/h`
- `delivery_person_speed = 20 km/h`

These parameters define the basic operational setting of the experiments.

---

### 2.2 `locker_info.csv`

This file contains the parcel locker information used in all instances.

#### Columns
- `locker_ID`: unique locker ID
- `locker_name`: locker name
- `lng`: longitude
- `lat`: latitude

#### Notes
- The locker set is fixed across all generated instances.
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

### 2.4 `order_instance_group_999/`

This folder contains a batch of generated experimental instance files.

Each file in this folder corresponds to one specific instance and includes:
1. selected drone launching stations;
2. generated customer orders.

Typical files include:
- `A_10_1.xlsx`
- `A_10_2.xlsx`
- ...
- `A_20_1.xlsx`
- `A_20_2.xlsx`

Among them, `A_10_1.xlsx` is one batch-generated instance file.

---

## 3. Instance File Format

Each instance file in `order_instance_group_999/` contains two parts.

### 3.1 Station information

The first part records the selected stations.

#### Columns
- `station_ID`: unique station ID
- `station_name`: station name
- `lng`: longitude
- `lat`: latitude

This part specifies the drone launching stations used in the instance.

---

### 3.2 Order information

The second part records the generated orders.

#### Columns
- `order_ID`: unique order ID
- `org_lng`: longitude of the order origin
- `org_lat`: latitude of the order origin
- `des_lng`: longitude of the order destination
- `des_lat`: latitude of the order destination
- `start_time_in_minute`: order start time in minutes

This part specifies the delivery requests in the instance.

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

Therefore, files with the same first number belong to the same size group, while the second number distinguishes different randomly generated samples.

---

## 5. Data Generation Logic

The instance data are generated based on real geographic information.

### Step 1: Candidate stations
Candidate stations are taken from the shopping center dataset.

### Step 2: Locker setting
The locker set is fixed and directly taken from `locker_info.csv`.

### Step 3: Station selection
A subset of shopping centers is selected as drone launching stations for each instance.

### Step 4: Order generation
For each order:
- an origin and a destination are generated;
- the origin must be reachable from at least one selected station;
- the destination must be reachable to at least one locker.

Only feasible orders are retained.

### Step 5: Time assignment
Each feasible order is assigned a random start time within the decision period, recorded in minutes.

---

## 6. Example: `A_10_1.xlsx`

This file is one generated instance in `order_instance_group_999/`.

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

---

## 7. Notes

1. Longitude and latitude are given in geographic coordinates.
2. Geographic distances should be computed using an appropriate distance formula when needed.
3. The locker dataset is fixed for all instances.
4. Station sets and order sets vary across different instance files.
5. The folder `order_instance_group_999` is a collection of batch-generated instances.

---

## 8. Summary

In summary:

- `parameters(1).txt` stores the main experimental parameters;
- `locker_info.csv` stores the fixed locker data;
- `shenzhen_shopping_centers(candidate_drone_launching_stations).xlsx` stores the candidate station data;
- `order_instance_group_999/` stores the generated instance files;
- files such as `A_10_1.xlsx` are individual batch-generated instance files containing both station and order information.

These files together form the complete dataset for the computational experiments.
