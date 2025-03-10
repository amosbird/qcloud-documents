自2021年01月起，增强型 SSD 云硬盘的单盘性能由**基准性能**和**额外性能**共同组成，其中：
- 基准性能与云硬盘容量呈线性关系，并在临界点达到基准性能的最大值。
- 若用户有超过基准性能的需求，可以选择开启配置额外性能，以获取更大的单盘性能。

本文将分别对基准性能和额外性能进行介绍。

## 增强型 SSD 云硬盘总性能

每块增强型 SSD 云硬盘的性能均由**基准性能**和**额外性能**两部分共同组成。不管如何分配，当前增强型 SSD 云硬盘的性能遵循以下规则：

| 增强型 SSD 云硬盘性能 | 最大值 |
| --------------------- | ------ |
| 随机 IOPS             | 100000 |
| 最大吞吐量（MB/s）    | 1000   |



## 增强型 SSD 云硬盘基准性能

对于增强型 SSD 云硬盘而言，基准性能随容量线性变化，不能独立调整。计算公式如下：

| 增强型 SSD 云硬盘基准性能    | 基准性能计算公式            | 基准性能最大值 |
| ---------------------------- | --------------------------- | -------------- |
| 基准性能 - 随机 IOPS         | min{1800 + 容量（GB）× 50, 50000} | 50000          |
| 基准性能 - 最大吞吐量（MB/s） | min{120 + 容量（GB）× 0.5, 350}   | 350            |

可以根据上述公式计算出：

- 在容量达到 460GB 时，首先达到吞吐量上限。此时基准性能值为：24800 随机 IOPS，350MB/s 最大吞吐量。
- 在容量达到 964GB 时，达到随机 IOPS 上限。此时基准性能值为：50000 随机 IOPS，350MB/s 最大吞吐量。



## 增强型 SSD 云硬盘额外性能

若用户有超过基准性能最大值的需求，可开启额外性能配置能力以获得更高性能。

### 前提条件

开启额外性能能力必须具备以下条件：

- 当前仅**增强型 SSD 云硬盘**和**极速型 SSD 云硬盘**两种产品类型支持额外性能，其他类型云硬盘暂不支持。
- 只在基准性能的任意一项达到最大值后才可配置额外性能。根据基准性能计算公式，即需要容量 > 460GB 时才支持。

### 额外性能计算公式

额外性能由用户自行配置，计算公式如下：

| 增强型 SSD 云硬盘额外性能    | 额外性能计算公式      | 额外性能最大值 |
| ---------------------------- | --------------------- | -------------- |
| 额外性能 - 随机 IOPS         | min{配置值 × 128, 50000} | 50000          |
| 额外性能 - 最大吞吐量（MB/s） | min{配置值 × 1, 650}     | 650            |

### 额外性能价格
额外性能价格请参见 [价格总览](https://cloud.tencent.com/document/product/362/2413#performance)。

## 示例

**示例一：增强型 SSD 云硬盘，容量需求2000GB，吞吐量需求500MB/s。**

通过基准性能说明，可知该配置容量下已经达到基准性能（吞吐量）上限。为了满足需求，需要购买额外性能为 (500-350)/1 = 150。因此，总体需要购买的配置为：2000GB增强型 SSD 云硬盘，额外性能配置为 150。

**示例二：增强型 SSD 云硬盘，容量需求1000GB，IOPS 需求 50000。**
通过基准性能说明，可知该配置容量下已达到基准性能（随机 IOPS）上限。但用户无需更多 IOPS 性能需求，则无需配置额外性能。因此，总体需要购买的配置为：1000GB增强型 SSD 云硬盘，无额外性能。

