---
title: LabVIEW&Python
date: 2024-05-24 16:36:52
tags:
  - LabVIEW
  - Python
---

## pip install

[pip 安裝套件](https://www.maxlist.xyz/2019/07/13/pip-install-python/)

## Python Node (LabVIEW)

Python Node 是 LabVIEW 中可以直接執行 py Code 的一個方式，於執行系統中必須先安裝對應版本的 Python，並透過 pip 預先安裝所需使用的 Modules 即可。

<!--more-->

![Untitled.png](./images/LabVIEW-Python/Untitled.png)

欲以 Node 執行 py 程式碼，必須於指定的 py 檔中，將程式碼以 def 的形式包成可以呼叫的狀態，並透過 return 將資料拋回 LabVIEW，如下：

```python
import numpy as np

def pyULE(input_times,dir_of_folders):
    # 轉換成 nparray 以供 python 使用
    time_all_folder = np.array(input_times)
    # 轉換成 list 拋回 LabVIEW
    rtnarray = time_all_folder.tolist()
    return rtnarray
```

由 LabVIEW 將數據導入至 Python 時，由於 Python 自動認定導入數值為 List 型態，故須將數據先轉為 Array，以提供 python 進行數據分析

```python
# 轉換成 nparray 以供 python 使用
time_all_folder = np.array(input_times)
```

最終在轉拋回 LabVIEW 時，將 npArray 轉回 List

```python
# 轉換成 list 拋回 LabVIEW
rtnarray = time_all_folder.tolist()
return rtnarray
```

輸入後轉換在拋出，確認資料經過轉換後並沒有損失或差異。

![Untitled 1](./images/LabVIEW-Python/Untitled1.png)
