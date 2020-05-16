# go_job_queue

## 使用job  queue 用來處理 耗時的 task

關鍵在於 channel數量的多寡 與實際上會放入的channel的數目有關

假設今天 channel設定buffer為 10

則放入第11個job時

這個job就會被block

因此要思考如何處理 block機制

1 用select來判目前channel是否滿

來決定是否寫入

2 用另一個go runtine讓 這個 新的job block在background不要block原本的程式