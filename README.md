1. Download Animal Face High Quality v2
```
bash download.sh afhq-v2-dataset
```

2. Split test to make val
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

3. Create txt files for dataloader
```
find "$(pwd)/data/train" -name "*.png" > train.txt
find "$(pwd)/data/val" -name "*.png" > val.txt
find "$(pwd)/data/test" -name "*.png" > test.txt
```

### Citation
```
StarGAN v2
Copyright (c) 2020-present NAVER Corp.

This work is licensed under the Creative Commons Attribution-NonCommercial
4.0 International License. To view a copy of this license, visit
http://creativecommons.org/licenses/by-nc/4.0/ or send a letter to
Creative Commons, PO Box 1866, Mountain View, CA 94042, USA.
```
