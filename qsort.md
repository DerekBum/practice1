```c++
int Partition(vector<int>& values, int l, int r) {
  int x = values[r];
  int less = l;

  for (int i = l; i < r; ++i) {
    if (values[i] <= x) {
      swap(values[i], values[less]);
      ++less;
    }
  }
  swap(values[less], values[r]);
  return less;
}

void QuickSortImpl(vector<int>& values, int l, int r) {
  if (l < r) {
    int q = Partition(values, l, r);
    QuickSortImpl(values, l, q - 1);
    QuickSortImpl(values, q + 1, r);
  }
}

void QuickSort(vector<int>& values) {
  if (!values.empty()) {
    QuickSortImpl(values, 0, values.size() - 1);
  }
}
```
---

Сначала из массива нужно выбрать один элемент — его обычно называют опорным. Затем другие элементы в массиве перераспределяют так, чтобы элементы меньше опорного оказались до него, а большие или равные — после. А дальше рекурсивно применяют первые два шага к подмассивам справа и слева от опорного значения.
