# Menjalankan Worker

* Membuka file `greeting.py`
* Menjalankan file `worker.py`
* Jalankan perintah

```
temporal workflow start \
    --type GreetSomeone \
    --task-queue greeting-tasks \
    --workflow-id my-first-workflow \
    --input '"Mason"' 
```
