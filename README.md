1. 

```
bash download.sh afhq-v2-dataset
```

2.

```
for d in data/test/*; do
  if [ -d "$d" ]; then
    class_name=$(basename "$d")
    mkdir -p "data/val/$class_name"
    files=("$d"/*.png)
    move_count=$((${#files[@]} / 2))
    for ((i=0; i<move_count; i++)); do
      mv "${files[i]}" "data/val/$class_name/"
    done
  fi
done
```

3.
```
find "$(pwd)/data/train" -name "*.png" > train.txt
find "$(pwd)/data/val" -name "*.png" > val.txt
find "$(pwd)/data/test" -name "*.png" > test.txt
```
