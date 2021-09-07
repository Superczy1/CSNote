### . Graph

* Dijistra: 求从源点到其他点的距离

  ```java
  int[] dist = new int[n];
  Arrays.fill(dist, INF);
  dist[k - 1] = 0;
  boolean[] used = new boolean[n];
  //每次确定一个 目标
  for (int i = 0; i < n; ++i) {
      int x = -1;
      //找到 dist 最小的起点
      for (int y = 0; y < n; ++y) {
          if (!used[y] && (x == -1 || dist[y] < dist[x])) {
              x = y;
          }
      }
      used[x] = true;
      // 开始更新 dist
      for (int y = 0; y < n; ++y) {
          dist[y] = Math.min(dist[y], dist[x] + g[x][y]);
      }
  }
  
  ```

  