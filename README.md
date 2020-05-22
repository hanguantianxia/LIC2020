[TOC]

```python
#!/data/anaconda3/bin/python
# -*- coding: utf-8 -*-
```



```shell
rsync -avzu --progress output_data_join_utf8/ lat@10.108.218.217:/home_export/lat/output_data_join_utf8/
rsync -avzu --progress output_roberta_utf8/ lat@10.108.218.217:/home_export/lat/output_roberta_utf8/
rsync -avzu --progress data_join/ lat@10.108.218.217:/home_export/lat/data_join/
rsync -avzu --progress output_albert_xxlarge_utf8/ lat@10.108.218.217:/home_export/lat/output_albert_xxlarge_utf8/
rsync -avzu --progress all_logit_0504/ lat@10.108.218.217:/home_export/lat/all_logit_0504/
rsync -avzu --progress all_logit_0505/ lat@10.108.218.217:/home_export/lat/all_logit_0505/
rsync -avzu --progress all_logit_0508/ lat@10.108.218.217:/home_export/lat/all_logit_0508/
rsync -avzu --progress output_test2/ lat@10.108.218.217:/home_export/lat/output_test2/
```



#  ChineseMRC代码确定后



## Data Join

### V1

cetc500+baidushort+cmrc+lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/chinese-roberta-wwm-ext-large --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v1 --model_type bert --train_file train_cetc500_baidushort_cmrc_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v1/checkpoint-10409 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v1/ --model_type bert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 3906620984 4月  14 03:41 checkpoint-10409
drwxr-xr-x 1 mqq mqq 3906620984 4月  14 09:34 checkpoint-15613
drwxr-xr-x 1 mqq mqq 3906620984 4月  14 15:28 checkpoint-20817
drwxr-xr-x 1 mqq mqq 3906620984 4月  14 21:21 checkpoint-26021
drwxr-xr-x 1 mqq mqq 3906620984 4月  13 21:48 checkpoint-5205



### V2

cetc500+baidushort+cmrc+lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/albert_chinese_xxlarge --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v2 --model_type albert --train_file train_lsb_baidushort_cmrc_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 4 --do_train --learning_rate 2e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --overwrite_cache --gradient_accumulation_steps 8 --threads 4
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path  /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v2/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v2/ --model_type albert --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --overwrite_cache --gradient_accumulation_steps 8 --threads 4
```





### V3

baidushort+cmrc+lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/albert_chinese_xxlarge --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v3 --model_type albert --train_file train_baidushort_cmrc_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 4 --do_train --learning_rate 2e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 8 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v3/checkpoint-17607 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v3 --model_type albert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 8 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 2523494142 Apr 16 06:57 checkpoint-17607
drwxr-xr-x 1 mqq mqq 2523494142 Apr 17 17:35 checkpoint-26410
drwxr-xr-x 1 mqq mqq 2523494142 Apr 19 04:11 checkpoint-35213
drwxr-xr-x 1 mqq mqq 2523494142 Apr 20 14:47 checkpoint-44016
drwxr-xr-x 1 mqq mqq 2523494142 Apr 14 20:21 checkpoint-8804

### V4

baidushort+cmrc+lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/chinese-roberta-wwm-ext-large --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v4/baidushortcmrclic --model_type bert --train_file train_baidushort_cmrc_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v4/baidushortcmrclic/checkpoint-8804 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v4/baidushortcmrclic --model_type bert --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 3898224168 4月  14 03:08 checkpoint-17607
drwxr-xr-x 1 mqq mqq 3898224168 4月  14 10:41 checkpoint-26410
drwxr-xr-x 1 mqq mqq 3898224168 4月  14 18:16 checkpoint-35213
drwxr-xr-x 1 mqq mqq 3898224168 4月  15 01:49 checkpoint-44016
drwxr-xr-x 1 mqq mqq 3898224168 4月  13 19:34 checkpoint-8804


```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v4/baidushortcmrclic/checkpoint-44016 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v4/baidushortcmrclic_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```





### V5

baidushort+cmrc/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/chinese-roberta-wwm-ext-large --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v5/baidushortcmrc --model_type bert --train_file train_baidushort_cmrc.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v5/baidushortcmrc/checkpoint-15965 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v5/baidushortcmrc_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v5/baidushortcmrc_lic/checkpoint-4106 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v5/baidushortcmrc_lic --model_type bert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 3898223854 4月  14 05:15 checkpoint-15965
drwxr-xr-x 1 mqq mqq 3898223854 4月  13 22:22 checkpoint-7983

drwxr-xr-x 1 mqq mqq 1302306176 4月  15 12:36 checkpoint-1643
drwxr-xr-x 1 mqq mqq 1302306176 4月  15 13:18 checkpoint-2464
drwxr-xr-x 1 mqq mqq 1302306176 4月  15 14:01 checkpoint-3285
drwxr-xr-x 1 mqq mqq 1302306176 4月  15 14:43 checkpoint-4106
drwxr-xr-x 1 mqq mqq 1302306176 4月  15 11:54 checkpoint-822



### V6

cetc500+baidushort+cmrc/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/chinese-roberta-wwm-ext-large --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v6/cetc500baidushortcmrc --model_type bert --train_file train_cetc500_baidushort_cmrc.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v6/cetc500baidushortcmrc/checkpoint-19175 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v6/cetc500baidushortcmrc_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v6/cetc500baidushortcmrc_lic/checkpoint-3285 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v6/cetc500baidushortcmrc_lic --model_type bert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 3898224042 4月  14 07:58 checkpoint-19175
drwxr-xr-x 1 mqq mqq 3898224042 4月  13 23:43 checkpoint-9588



drwxr-xr-x 1 mqq mqq 1302306164 4月  15 12:38 checkpoint-1643
drwxr-xr-x 1 mqq mqq 1302306164 4月  15 13:21 checkpoint-2464
drwxr-xr-x 1 mqq mqq 1302306164 4月  15 14:03 checkpoint-3285
drwxr-xr-x 1 mqq mqq 1302306164 4月  15 14:45 checkpoint-4106
drwxr-xr-x 1 mqq mqq 1302306164 4月  15 11:56 checkpoint-822



### V7

cmrc/baidushort/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/chinese-roberta-wwm-ext-large --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v7/cmrc --model_type bert --train_file train_cmrc.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3  --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v7/cmrc/checkpoint-2985 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v7/cmrc_baidushort --model_type bert --train_file train_baidushort.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v7/cmrc_baidushort/checkpoint-12981 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v7/cmrc_baidushort_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v7/cmrc_baidushort/checkpoint-6491 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v7/cmrc_baidushort --model_type bert --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 3898215003 4月  13 14:34 checkpoint-1493
drwxr-xr-x 1 mqq mqq 3898215003 4月  13 15:51 checkpoint-2985

drwxr-xr-x 1 mqq mqq 1302306165 4月  15 22:06 checkpoint-12981
drwxr-xr-x 1 mqq mqq 1302306165 4月  15 16:30 checkpoint-6491

drwxr-xr-x 1 mqq mqq 1302306172 4月  16 00:45 checkpoint-1643
drwxr-xr-x 1 mqq mqq 1302306172 4月  16 01:28 checkpoint-2464
drwxr-xr-x 1 mqq mqq 1302306172 4月  16 02:10 checkpoint-3285
drwxr-xr-x 1 mqq mqq 1302306172 4月  16 02:52 checkpoint-4106
drwxr-xr-x 1 mqq mqq 1302306172 4月  16 00:03 checkpoint-822

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v7/cmrc/checkpoint-1493 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v7/cmrc1_baidushort --model_type bert --train_file train_baidushort.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

### V8

baidushort/cmrc/lic

Train

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/chinese-roberta-wwm-ext-large --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v8/baidushort --model_type bert --train_file train_baidushort.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v8/baidushort/checkpoint-12981 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v8/baidushort_cmrc --model_type bert --train_file train_cmrc.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v8/baidushort_cmrc/checkpoint-2985 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v8/baidushort_cmrc_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 3 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v8/baidushort_cmrc_lic/checkpoint-2464 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v8/baidushort_cmrc_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --inherit_global_step
```

predict

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v8/baidushort1_cmrc/checkpoint-1493 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v8/baidushort1_cmrc --model_type bert --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 3898215005 4月  14 02:36 checkpoint-12981
drwxr-xr-x 1 mqq mqq 3898215005 4月  13 21:01 checkpoint-6491

drwxr-xr-x 1 mqq mqq 1302306168 4月  15 01:20 checkpoint-1493
drwxr-xr-x 1 mqq mqq 1302306168 4月  15 02:37 checkpoint-2985

drwxr-xr-x 1 mqq mqq 1302306169 4月  15 11:56 checkpoint-1643
drwxr-xr-x 1 mqq mqq 1302306169 4月  15 12:38 checkpoint-2464
drwxr-xr-x 1 mqq mqq 1302306173 4月  15 14:23 checkpoint-3285
drwxr-xr-x 1 mqq mqq 1302306173 4月  15 15:05 checkpoint-4106
drwxr-xr-x 1 mqq mqq 1302306169 4月  15 11:13 checkpoint-822

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v8/baidushort/checkpoint-6491 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v8/baidushort1_cmrc --model_type bert --train_file train_cmrc.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v8/baidushort_cmrc_lic/checkpoint-2464 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v8/baidushort_cmrc_lic --model_type bert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_all_logit
```



### V9

cetc1500/baidushort+cmrc/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/chinese-roberta-wwm-ext-large --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v9/cetc1500 --model_type bert --train_file train_cetc1500.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3--model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v9/cetc1500/checkpoint-15595 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v9/cetc1500_baidushortcmrc --model_type bert --train_file train_baidushort_cmrc.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v9/cetc1500_baidushortcmrc/checkpoint-15965 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v9/cetc1500_baidushortcmrc_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v9/cetc1500_baidushortcmrc/checkpoint-7983 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v9/cetc1500_baidushortcmrc/ --model_type bert --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 3898224065 4月  14 04:55 checkpoint-15595
drwxr-xr-x 1 mqq mqq 3898224065 4月  13 22:11 checkpoint-7798

drwxr-xr-x 1 mqq mqq 1302306179 4月  16 01:37 checkpoint-15965
drwxr-xr-x 1 mqq mqq 1302306179 4月  15 18:44 checkpoint-7983

drwxr-xr-x 1 mqq mqq 1302306168 4月  16 10:30 checkpoint-1643
drwxr-xr-x 1 mqq mqq 1302306168 4月  16 11:12 checkpoint-2464
drwxr-xr-x 1 mqq mqq 1302306168 4月  16 11:55 checkpoint-3285
drwxr-xr-x 1 mqq mqq 1302306168 4月  16 12:37 checkpoint-4106
drwxr-xr-x 1 mqq mqq 1302306168 4月  16 09:48 checkpoint-822

### V10

baidushort/cmrc/drcd/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v8/baidushort_cmrc/checkpoint-2985 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v10/baidushort_cmrc_drcd --model_type bert --train_file train_drcd.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v10/baidushort_cmrc_drcd/checkpoint-5137 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v10/baidushort_cmrc_drcd_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v10/baidushort_cmrc_drcd_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v10/baidushort_cmrc_drcd_lic --model_type bert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 1302306158 4月  18 19:04 checkpoint-2569
drwxr-xr-x 1 mqq mqq 1302306158 4月  18 21:17 checkpoint-5137

drwxr-xr-x 1 mqq mqq 1302306197 4月  18 23:42 checkpoint-1643
drwxr-xr-x 1 mqq mqq 1302306197 4月  19 00:24 checkpoint-2464
drwxr-xr-x 1 mqq mqq 1302306197 4月  19 01:07 checkpoint-3285
drwxr-xr-x 1 mqq mqq 1302306197 4月  19 01:49 checkpoint-4106
drwxr-xr-x 1 mqq mqq 1302306197 4月  18 23:00 checkpoint-822

### V11

baidushort/cmrc/dureader

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v8/baidushort_cmrc/checkpoint-2985 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v11/baidushort_cmrc_dureader --model_type bert --train_file train_dureader.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v11/baidushort_cmrc_dureader/checkpoint-10001 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v11/baidushort_cmrc_dureader_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v11/baidushort_cmrc_dureader_lic/checkpoint-2464 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v11/baidushort_cmrc_dureader_lic --model_type bert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 1302306194 4月  21 08:18 checkpoint-10001
drwxr-xr-x 1 mqq mqq 1302306194 4月  21 04:00 checkpoint-5001

### V12

baidushort/cmrc/cail/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v8/baidushort_cmrc/checkpoint-2985 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v12/baidushort_cmrc_cail --model_type bert --train_file train_cail.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v12/baidushort_cmrc_cail/checkpoint-7747 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v12/baidushort_cmrc_cail_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v12/baidushort_cmrc_cail/checkpoint-3874 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v12/baidushort_cmrc_cail --model_type bert --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 1302306170 4月  21 03:01 checkpoint-3874
drwxr-xr-x 1 mqq mqq 1302306170 4月  21 06:21 checkpoint-7747

drwxr-xr-x 1 mqq mqq 1302306181 Apr 21 12:23 checkpoint-1643
drwxr-xr-x 1 mqq mqq 1302306181 Apr 21 13:05 checkpoint-2464
drwxr-xr-x 1 mqq mqq 1302306181 Apr 21 13:48 checkpoint-3285
drwxr-xr-x 1 mqq mqq 1302306181 Apr 21 14:30 checkpoint-4106
drwxr-xr-x 1 mqq mqq 1302306181 Apr 21 11:41 checkpoint-822

### V13

lic_extended_v1

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/chinese-roberta-wwm-ext-large --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v13 --model_type bert --train_file train_extended_v1.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v13/checkpoint-9271 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v13 --model_type bert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 1302306010 Apr 23 01:21 checkpoint-1855
drwxr-xr-x 1 mqq mqq 1302306010 Apr 23 02:56 checkpoint-3709
drwxr-xr-x 1 mqq mqq 1302306010 Apr 23 04:32 checkpoint-5563
drwxr-xr-x 1 mqq mqq 1302306010 Apr 23 06:07 checkpoint-7417
drwxr-xr-x 1 mqq mqq 1302306010 Apr 23 07:43 checkpoint-9271



### V14

baidushort/cmrc/drcd/cail/cetc1500/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v10/baidushort_cmrc_drcd/checkpoint-5137 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14/baidushort_cmrc_drcd_cail --model_type bert --train_file train_cail.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14/baidushort_cmrc_drcd_cail/checkpoint-7747 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14/baidushort_cmrc_drcd_cail_cetc1500 --model_type bert --train_file train_cetc1500.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14/baidushort_cmrc_drcd_cail_cetc1500/checkpoint-15595 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14/baidushort_cmrc_drcd_cail_cetc1500_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14/baidushort_cmrc_drcd_cail_cetc1500_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14/baidushort_cmrc_drcd_cail_cetc1500_lic --model_type bert --predict_file train_lic.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 1302306185 Apr 24 02:16 checkpoint-3874
drwxr-xr-x 1 mqq mqq 1302306185 Apr 24 05:36 checkpoint-7747

drwxr-xr-x 1 mqq mqq 1302306195 4月  25 06:29 checkpoint-15595
drwxr-xr-x 1 mqq mqq 1302306195 4月  24 23:47 checkpoint-7798

drwxr-xr-x 1 mqq mqq 1302306202 4月  25 15:00 checkpoint-1643
drwxr-xr-x 1 mqq mqq 1302306202 4月  25 15:42 checkpoint-2464
drwxr-xr-x 1 mqq mqq 1302306202 4月  25 16:25 checkpoint-3285
drwxr-xr-x 1 mqq mqq 1302306202 4月  25 17:07 checkpoint-4106
drwxr-xr-x 1 mqq mqq 1302306202 4月  25 14:17 checkpoint-822

```shell
python test_multi_2.py 
--data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_type bert --predict_file test2_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --max_answer_length 40 --per_gpu_eval_batch_size 8 --n_best_size 20 --split_doc --do_lower_case --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14/baidushort_cmrc_drcd_cail_cetc1500_lic/checkpoint-4106 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14/baidushort_cmrc_drcd_cail_cetc1500_lic/checkpoint-3285 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14/baidushort_cmrc_drcd_cail_cetc1500_lic/checkpoint-2464 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14/baidushort_cmrc_drcd_cail_cetc1500_lic/checkpoint-1643 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14/baidushort_cmrc_drcd_cail_cetc1500_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14/baidushort_cmrc_drcd_cail_cetc1500_lic
```

### V14_2

baidushort/cmrc/drcd/cail/cetc1500/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v43/webqa_epoch2 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14_2/baidushort --model_type bert --train_file train_baidushort.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14_2/baidushort
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14_2/baidushort/checkpoint-6491 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14_2/baidushort1_cmrc --model_type bert --train_file train_cmrc.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 1 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14_2/baidushort1_cmrc
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14_2/baidushort1_cmrc/checkpoint-1493 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14_2/baidushort1_cmrc1_drcd --model_type bert --train_file train_drcd.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 1 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14_2/baidushort1_cmrc1_drcd
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14_2/baidushort1_cmrc1_drcd/checkpoint-2569 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14_2/baidushort1_cmrc1_drcd1_cail --model_type bert --train_file train_cail.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 1 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14_2/baidushort1_cmrc1_drcd1_cail
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14_2/baidushort1_cmrc1_drcd1_cail/checkpoint-3874 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14_2/baidushort1_cmrc1_drcd1_cail1_cetc1500 --model_type bert --train_file train_cetc1500.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 1 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14_2/baidushort1_cmrc1_drcd1_cail1_cetc1500
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14_2/baidushort1_cmrc1_drcd1_cail1_cetc1500/checkpoint-7798 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14_2/baidushort1_cmrc1_drcd1_cail1_cetc15001_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14_2/baidushort1_cmrc1_drcd1_cail1_cetc15001_lic
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14/baidushort_cmrc_drcd_cail_cetc1500_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14/baidushort_cmrc_drcd_cail_cetc1500_lic --model_type bert --predict_file train_lic.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python test_multi_2.py 
--data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_type bert --predict_file test2_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --max_answer_length 40 --per_gpu_eval_batch_size 8 --n_best_size 20 --split_doc --do_lower_case --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14_2/baidushort1_cmrc1_drcd1_cail1_cetc15001_lic/checkpoint-2464 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14_2/baidushort1_cmrc1_drcd1_cail1_cetc15001_lic/checkpoint-4106 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14_2/baidushort1_cmrc1_drcd1_cail1_cetc15001_lic/checkpoint-3285 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14_2/baidushort1_cmrc1_drcd1_cail1_cetc15001_lic/checkpoint-1643 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14_2/baidushort1_cmrc1_drcd1_cail1_cetc15001_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14_2/baidushort1_cmrc1_drcd1_cail1_cetc15001_lic
```



### V15

lic_extended_v2/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/chinese-roberta-wwm-ext-large --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v15/lic_extended_v2 --model_type bert --train_file train_extended_v2.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v15/lic_extended_v2/checkpoint-2067 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v15/lic_extended_v2_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v15/lic_extended_v2_lic/checkpoint-2464 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v15/lic_extended_v2_lic --model_type bert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 1302306018 4月  24 18:09 checkpoint-1034
drwxr-xr-x 1 mqq mqq 1302306018 4月  24 19:03 checkpoint-2067

drwxr-xr-x 1 mqq mqq 1302306177 4月  25 15:55 checkpoint-1643
drwxr-xr-x 1 mqq mqq 1302306177 4月  25 16:37 checkpoint-2464
drwxr-xr-x 1 mqq mqq 1302306177 4月  25 17:19 checkpoint-3285
drwxr-xr-x 1 mqq mqq 1302306177 4月  25 18:02 checkpoint-4106
drwxr-xr-x 1 mqq mqq 1302306177 4月  25 15:12 checkpoint-822



### V16

baidushort/cmrc/cail1/cetc1500/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v12/baidushort_cmrc_cail/checkpoint-3874 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v16/baidushort2_cmrc2_cail1_cetc1500 --model_type bert --train_file train_cetc1500.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v16/baidushort2_cmrc2_cail1_cetc1500/checkpoint-7798 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v16/baidushort2_cmrc2_cail1_cetc15001_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v16/baidushort2_cmrc2_cail1_cetc15001_lic/checkpoint-1643 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v16/baidushort2_cmrc2_cail1_cetc15001_lic --model_type bert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 1302306196 4月  26 10:59 checkpoint-15595
drwxr-xr-x 1 mqq mqq 1302306196 4月  26 04:17 checkpoint-7798

drwxr-xr-x 1 mqq mqq 1302306200 Apr 26 13:39 checkpoint-1643
drwxr-xr-x 1 mqq mqq 1302306200 Apr 26 14:21 checkpoint-2464
drwxr-xr-x 1 mqq mqq 1302306200 Apr 26 15:04 checkpoint-3285
drwxr-xr-x 1 mqq mqq 1302306200 Apr 26 15:47 checkpoint-4106
drwxr-xr-x 1 mqq mqq 1302306200 Apr 26 12:56 checkpoint-822

### V17

baidushort/cmrc/drcd/cail1/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14/baidushort_cmrc_drcd_cail/checkpoint-3874 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v17/baidushort2_cmrc2_drcd2_cail1_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v17/baidushort2_cmrc2_drcd2_cail1_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v17/baidushort2_cmrc2_drcd2_cail1_lic --model_type bert --predict_file train_lic.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 1302306203 4月  25 23:49 checkpoint-1643
drwxr-xr-x 1 mqq mqq 1302306203 4月  26 00:32 checkpoint-2464
drwxr-xr-x 1 mqq mqq 1302306203 4月  26 01:14 checkpoint-3285
drwxr-xr-x 1 mqq mqq 1302306203 4月  26 01:56 checkpoint-4106
drwxr-xr-x 1 mqq mqq 1302306203 4月  25 23:07 checkpoint-822

```shell
python test_multi_2.py 
--data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_type bert --predict_file test2_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --max_answer_length 40 --per_gpu_eval_batch_size 8 --n_best_size 20 --split_doc --do_lower_case --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v17/baidushort2_cmrc2_drcd2_cail1_lic/checkpoint-4106 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v17/baidushort2_cmrc2_drcd2_cail1_lic/checkpoint-3285 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v17/baidushort2_cmrc2_drcd2_cail1_lic/checkpoint-2464 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v17/baidushort2_cmrc2_drcd2_cail1_lic/checkpoint-1643 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v17/baidushort2_cmrc2_drcd2_cail1_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v17/baidushort2_cmrc2_drcd2_cail1_lic
```

### V17_2

baidushort/cmrc/drcd/cail1/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14_2/baidushort1_cmrc1_drcd1_cail/checkpoint-3874 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v17_2/baidushort1_cmrc1_drcd1_cail1_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v17_2/baidushort1_cmrc1_drcd1_cail1_lic
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v17/baidushort2_cmrc2_drcd2_cail1_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v17/baidushort2_cmrc2_drcd2_cail1_lic --model_type bert --predict_file train_lic.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python test_multi_2.py 
--data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_type bert --predict_file test2_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --max_answer_length 40 --per_gpu_eval_batch_size 8 --n_best_size 20 --split_doc --do_lower_case --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v17_2/baidushort1_cmrc1_drcd1_cail1_lic/checkpoint-4106 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v17_2/baidushort1_cmrc1_drcd1_cail1_lic/checkpoint-3285 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v17_2/baidushort1_cmrc1_drcd1_cail1_lic/checkpoint-2464 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v17_2/baidushort1_cmrc1_drcd1_cail1_lic/checkpoint-1643 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v17_2/baidushort1_cmrc1_drcd1_cail1_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v17_2/baidushort1_cmrc1_drcd1_cail1_lic
```



### V18

cmrc1/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v7/cmrc/checkpoint-1493 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v18/cmrc1_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v18/cmrc1_lic/checkpoint-2464 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v18/cmrc1_lic --model_type bert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 1302306155 4月  25 23:50 checkpoint-1643
drwxr-xr-x 1 mqq mqq 1302306155 4月  26 00:32 checkpoint-2464
drwxr-xr-x 1 mqq mqq 1302306155 4月  26 01:14 checkpoint-3285
drwxr-xr-x 1 mqq mqq 1302306155 4月  26 01:57 checkpoint-4106
drwxr-xr-x 1 mqq mqq 1302306155 4月  25 23:07 checkpoint-822

### V19

baidushort1/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v8/baidushort/checkpoint-6491 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v19/baidushort1_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v19/baidushort1_lic/checkpoint-3285 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v19/baidushort1_lic --model_type bert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 1302306161 4月  25 23:50 checkpoint-1643
drwxr-xr-x 1 mqq mqq 1302306161 4月  26 00:33 checkpoint-2464
drwxr-xr-x 1 mqq mqq 1302306161 4月  26 01:15 checkpoint-3285
drwxr-xr-x 1 mqq mqq 1302306161 4月  26 01:57 checkpoint-4106
drwxr-xr-x 1 mqq mqq 1302306161 4月  25 23:08 checkpoint-822



### V20

cetc15002_lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v9/cetc1500/checkpoint-15595 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v20/cetc15002_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v20/cetc15002_lic/checkpoint-3285 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v20/cetc15002_lic --model_type bert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 1302306168 4月  25 23:51 checkpoint-1643
drwxr-xr-x 1 mqq mqq 1302306168 4月  26 00:33 checkpoint-2464
drwxr-xr-x 1 mqq mqq 1302306168 4月  26 01:15 checkpoint-3285
drwxr-xr-x 1 mqq mqq 1302306168 4月  26 01:58 checkpoint-4106
drwxr-xr-x 1 mqq mqq 1302306168 4月  25 23:08 checkpoint-822

### V21

drcd/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/chinese-roberta-wwm-ext-large --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v21/drcd --model_type bert --train_file train_drcd.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v21/drcd/checkpoint-2569 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v21/drcd1_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v21/drcd1_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v21/drcd1_lic --model_type bert --predict_file train_lic.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 1302306020 4月  26 00:40 checkpoint-2569
drwxr-xr-x 1 mqq mqq 1302306020 4月  26 02:53 checkpoint-5137

drwxr-xr-x 1 mqq mqq 1302306146 4月  26 14:16 checkpoint-1643
drwxr-xr-x 1 mqq mqq 1302306146 4月  26 14:59 checkpoint-2464
drwxr-xr-x 1 mqq mqq 1302306146 4月  26 15:41 checkpoint-3285
drwxr-xr-x 1 mqq mqq 1302306146 4月  26 16:23 checkpoint-4106
drwxr-xr-x 1 mqq mqq 1302306146 4月  26 13:34 checkpoint-822

```shell
python test_multi_2.py 
--data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_type bert --predict_file test2_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --max_answer_length 40 --per_gpu_eval_batch_size 8 --n_best_size 20 --split_doc --do_lower_case --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v21/drcd1_lic/checkpoint-4106 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v21/drcd1_lic/checkpoint-3285 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v21/drcd1_lic/checkpoint-2464 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v21/drcd1_lic/checkpoint-1643 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v21/drcd1_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v21/drcd1_lic
```

### V21_2

drcd/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v43/webqa_epoch2 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v21_2/drcd --model_type bert --train_file train_drcd.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v21_2/drcd
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v21_2/drcd/checkpoint-2569 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v21_2/drcd1_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v21_2/drcd1_lic
```

```shell
python test_multi_2.py 
--data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_type bert --predict_file test2_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --max_answer_length 40 --per_gpu_eval_batch_size 8 --n_best_size 20 --split_doc --do_lower_case --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v21_2/drcd1_lic/checkpoint-2464 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v21_2/drcd1_lic/checkpoint-1643 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v21_2/drcd1_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v21_2/drcd1_lic
```

 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v21_2/drcd1_lic/checkpoint-4106 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v21_2/drcd1_lic/checkpoint-3285

### V22

cail/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/chinese-roberta-wwm-ext-large --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v22/cail --model_type bert --train_file train_cail.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v22/cail/checkpoint-3874 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v22/cail1_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v22/cail1_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v22/cail1_lic --model_type bert --predict_file train_lic.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 1302306032 4月  26 01:48 checkpoint-3874
drwxr-xr-x 1 mqq mqq 1302306032 4月  26 05:08 checkpoint-7747

drwxr-xr-x 1 mqq mqq 1302306142 4月  26 14:16 checkpoint-1643
drwxr-xr-x 1 mqq mqq 1302306142 4月  26 14:59 checkpoint-2464
drwxr-xr-x 1 mqq mqq 1302306142 4月  26 15:41 checkpoint-3285
drwxr-xr-x 1 mqq mqq 1302306142 4月  26 16:24 checkpoint-4106
drwxr-xr-x 1 mqq mqq 1302306142 4月  26 13:34 checkpoint-822

```shell
python test_multi_2.py 
--data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_type bert --predict_file test2_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --max_answer_length 40 --per_gpu_eval_batch_size 8 --n_best_size 20 --split_doc --do_lower_case --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v22/cail1_lic/checkpoint-4106 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v22/cail1_lic/checkpoint-3285 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v22/cail1_lic/checkpoint-2464 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v22/cail1_lic/checkpoint-1643 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v22/cail1_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v22/cail1_lic
```

### V22_2

cail/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v43/webqa_epoch2 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v22_2/cail --model_type bert --train_file train_cail.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v22_2/cail
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v22_2/cail/checkpoint-3874 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v22_2/cail1_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v22_2/cail1_lic
```

```shell
python test_multi_2.py 
--data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_type bert --predict_file test2_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --max_answer_length 40 --per_gpu_eval_batch_size 8 --n_best_size 20 --split_doc --do_lower_case --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v22_2/cail1_lic/checkpoint-3285 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v22_2/cail1_lic/checkpoint-2464 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v22_2/cail1_lic/checkpoint-1643 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v22_2/cail1_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v22_2/cail1_lic
```



### V23

cmrc1/drcd/cail/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v7/cmrc/checkpoint-1493 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23/cmrc1_drcd --model_type bert --train_file train_drcd.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23/cmrc1_drcd/checkpoint-2569 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23/cmrc1_drcd1_cail --model_type bert --train_file train_cail.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23/cmrc1_drcd1_cail/checkpoint-3874 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23/cmrc1_drcd1_cail1_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23/cmrc1_drcd1_cail1_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23/cmrc1_drcd1_cail1_lic --model_type bert --predict_file train_lic.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 12 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 1302306153 Apr 27 13:36 checkpoint-2569
drwxr-xr-x 1 mqq mqq 1302306153 Apr 27 15:48 checkpoint-5137

drwxr-xr-x 1 mqq mqq 1302306176 Apr 27 19:45 checkpoint-3874
drwxr-xr-x 1 mqq mqq 1302306176 Apr 27 23:05 checkpoint-7747

drwxr-xr-x 1 mqq mqq 1302306180 Apr 28 00:50 checkpoint-1643
drwxr-xr-x 1 mqq mqq 1302306180 Apr 28 01:32 checkpoint-2464
drwxr-xr-x 1 mqq mqq 1302306180 Apr 28 02:14 checkpoint-3285
drwxr-xr-x 1 mqq mqq 1302306180 Apr 28 02:57 checkpoint-4106
drwxr-xr-x 1 mqq mqq 1302306180 Apr 28 00:07 checkpoint-822

```shell
python test_multi_2.py 
--data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_type bert --predict_file test2_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --max_answer_length 40 --per_gpu_eval_batch_size 8 --n_best_size 20 --split_doc --do_lower_case --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23/cmrc1_drcd1_cail1_lic/checkpoint-4106 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23/cmrc1_drcd1_cail1_lic/checkpoint-3285 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23/cmrc1_drcd1_cail1_lic/checkpoint-2464 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23/cmrc1_drcd1_cail1_lic/checkpoint-1643 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23/cmrc1_drcd1_cail1_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23/cmrc1_drcd1_cail1_lic
```

### V23_2

cmrc1/drcd/cail/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v43/webqa_epoch2 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23_2/cmrc --model_type bert --train_file train_cmrc.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23_2/cmrc
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23_2/cmrc/checkpoint-1493 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23_2/cmrc1_drcd --model_type bert --train_file train_drcd.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 1 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23_2/cmrc1_drcd
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23_2/cmrc1_drcd/checkpoint-2569 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23_2/cmrc1_drcd1_cail --model_type bert --train_file train_cail.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 1 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23_2/cmrc1_drcd1_cail
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23_2/cmrc1_drcd1_cail/checkpoint-3874 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23_2/cmrc1_drcd1_cail1_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23_2/cmrc1_drcd1_cail1_lic
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23_2/cmrc1_drcd1_cail1_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23_2/cmrc1_drcd1_cail1_lic --model_type bert --predict_file train_lic.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 12 --model_name chinese-roberta-wwm-ext-large
```

```shell
python test_multi_2.py 
--data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_type bert --predict_file test2_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --max_answer_length 40 --per_gpu_eval_batch_size 8 --n_best_size 20 --split_doc --do_lower_case --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23_2/cmrc1_drcd1_cail1_lic/checkpoint-4106 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23_2/cmrc1_drcd1_cail1_lic/checkpoint-1643 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23_2/cmrc1_drcd1_cail1_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23_2/cmrc1_drcd1_cail1_lic
```

 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23_2/cmrc1_drcd1_cail1_lic/checkpoint-3285 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23_2/cmrc1_drcd1_cail1_lic/checkpoint-2464 

### V24

lic_extended_v3/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/chinese-roberta-wwm-ext-large --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v24/lic_extended_v3 --model_type bert --train_file train_extended_v3.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v24/lic_extended_v3/checkpoint-1959 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v24/lic_extended_v3_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v24/lic_extended_v3_lic/checkpoint-2464 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v24/lic_extended_v3_lic --model_type bert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 1302306028 Apr 28 00:57 checkpoint-1959
drwxr-xr-x 1 mqq mqq 1302306028 Apr 28 00:07 checkpoint-980

drwxr-xr-x 1 mqq mqq 1302306169 Apr 28 11:59 checkpoint-1643
drwxr-xr-x 1 mqq mqq 1302306169 Apr 28 12:41 checkpoint-2464
drwxr-xr-x 1 mqq mqq 1302306169 Apr 28 13:23 checkpoint-3285
drwxr-xr-x 1 mqq mqq 1302306169 Apr 28 14:06 checkpoint-4106
drwxr-xr-x 1 mqq mqq 1302306169 Apr 28 11:16 checkpoint-822



### V25

cmrc1/drcd/cail/lic（albert-xxlarge）

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/albert_chinese_xxlarge --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v25/cmrc --model_type albert --train_file train_cmrc.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 4 --do_train --learning_rate 2e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 8 --threads 3 --model_name albert_chinese_xxlarge
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v25/cmrc/checkpoint-2985 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v25/cmrc2_drcd --model_type albert --train_file train_drcd.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 4 --do_train --learning_rate 2e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 8 --threads 3 --model_name albert_chinese_xxlarge
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v25/cmrc2_drcd/checkpoint-2569 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v25/cmrc2_drcd1_cail --model_type albert --train_file train_cail.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 4 --do_train --learning_rate 2e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 8 --threads 3 --model_name albert_chinese_xxlarge
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v25/cmrc2_drcd1_cail/checkpoint-3874 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v25/cmrc2_drcd1_cail1_lic --model_type albert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 4 --do_train --learning_rate 2e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 8 --threads 3 --model_name albert_chinese_xxlarge
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v25/cmrc2_drcd1_cail1_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v25/cmrc2_drcd1_cail1_lic --model_type albert --predict_file train_lic.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 8 --threads 12 --model_name albert_chinese_xxlarge
```

drwxr-xr-x 1 mqq mqq 885991842 Apr 29 06:09 checkpoint-1493
drwxr-xr-x 1 mqq mqq 885991842 Apr 29 11:59 checkpoint-2985

drwxr-xr-x 1 mqq mqq 885991875 Apr 30 22:50 checkpoint-2569
drwxr-xr-x 1 mqq mqq 885991875 May  1 09:00 checkpoint-5137

drwxr-xr-x 1 mqq mqq 885991911 May  2 02:14 checkpoint-3874
drwxr-xr-x 1 mqq mqq 885991911 May  2 17:28 checkpoint-7747

drwxr-xr-x 1 mqq mqq 885991921 May  3 03:09 checkpoint-1643
drwxr-xr-x 1 mqq mqq 885991921 May  3 06:21 checkpoint-2464
drwxr-xr-x 1 mqq mqq 885991921 May  3 09:33 checkpoint-3285
drwxr-xr-x 1 mqq mqq 885991921 May  3 12:46 checkpoint-4106
drwxr-xr-x 1 mqq mqq 885991921 May  2 23:57 checkpoint-822

```shell
python test_multi_2.py 
--data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_type albert --predict_file test2_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --max_answer_length 40 --per_gpu_eval_batch_size 8 --n_best_size 20 --split_doc --do_lower_case --threads 12 --model_name albert_chinese_xxlarge --output_all_logit --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v25/cmrc2_drcd1_cail1_lic/checkpoint-4106 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v25/cmrc2_drcd1_cail1_lic/checkpoint-3285 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v25/cmrc2_drcd1_cail1_lic/checkpoint-2464 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v25/cmrc2_drcd1_cail1_lic/checkpoint-1643 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v25/cmrc2_drcd1_cail1_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v25/cmrc2_drcd1_cail1_lic
```



### V26

cmrc1/drcd1/cail1/lic（roberta-large 512）

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/chinese-roberta-wwm-ext-large --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v26/cmrc --model_type bert --train_file train_cmrc.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 512 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 4 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 8 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v26/cmrc/checkpoint-761 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v26/cmrc1_drcd --model_type bert --train_file train_drcd.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 512 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 4 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 8 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v26/cmrc1_drcd/checkpoint-1201 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v26/cmrc1_drcd1_cail --model_type bert --train_file train_cail.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 512 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 4 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 8 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v26/cmrc1_drcd1_cail/checkpoint-2258 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v26/cmrc1_drcd1_cail1_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 512 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 4 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 8 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v26/cmrc1_drcd1_cail1_lic/checkpoint-553 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v26/cmrc1_drcd1_cail1_lic --model_type bert --predict_file train_lic.json --do_eval --overwrite_output_dir --max_seq_length 512 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 8 --threads 12 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 1302306014 Apr 29 03:13 checkpoint-1521
drwxr-xr-x 1 mqq mqq 1302306014 Apr 29 01:47 checkpoint-761

drwxr-xr-x 1 mqq mqq 1302306147 Apr 29 12:23 checkpoint-1201
drwxr-xr-x 1 mqq mqq 1302306147 Apr 29 14:39 checkpoint-2401

drwxr-xr-x 1 mqq mqq 1302306152 Apr 30 15:41 checkpoint-2258
drwxr-xr-x 1 mqq mqq 1302306152 Apr 30 19:56 checkpoint-4515

drwxr-xr-x 1 mqq mqq 1302306198 May  1 01:59 checkpoint-1105
drwxr-xr-x 1 mqq mqq 1302306198 May  1 03:01 checkpoint-1657
drwxr-xr-x 1 mqq mqq 1302306198 May  1 04:04 checkpoint-2209
drwxr-xr-x 1 mqq mqq 1302306198 May  1 05:06 checkpoint-2761
drwxr-xr-x 1 mqq mqq 1302306198 May  1 00:56 checkpoint-553

```shell
python test_multi_2.py 
--data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_type bert --predict_file test2_dealed.json --do_eval --overwrite_output_dir --max_seq_length 512 --max_answer_length 40 --per_gpu_eval_batch_size 8 --n_best_size 20 --split_doc --do_lower_case --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v26/cmrc1_drcd1_cail1_lic/checkpoint-2761 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v26/cmrc1_drcd1_cail1_lic/checkpoint-2209 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v26/cmrc1_drcd1_cail1_lic/checkpoint-1657 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v26/cmrc1_drcd1_cail1_lic/checkpoint-1105 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v26/cmrc1_drcd1_cail1_lic/checkpoint-553 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v26/cmrc1_drcd1_cail1_lic
```

### V26_2

cmrc1/drcd1/cail1/lic（roberta-large 512）

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v43/webqa_epoch2 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v26_2/cmrc --model_type bert --train_file train_cmrc.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 512 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 4 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 8 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v26_2/cmrc
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v26_2/cmrc/checkpoint-761 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v26_2/cmrc1_drcd --model_type bert --train_file train_drcd.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 512 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 4 --do_train --learning_rate 3e-5 --num_train_epochs 1 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 8 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v26_2/cmrc1_drcd
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v26_2/cmrc1_drcd/checkpoint-1201 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v26_2/cmrc1_drcd1_cail --model_type bert --train_file train_cail.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 512 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 4 --do_train --learning_rate 3e-5 --num_train_epochs 1 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 8 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v26_2/cmrc1_drcd1_cail
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v26_2/cmrc1_drcd1_cail/checkpoint-2258 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v26_2/cmrc1_drcd1_cail1_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 512 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 4 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 8 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v26_2/cmrc1_drcd1_cail1_lic
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v26/cmrc1_drcd1_cail1_lic/checkpoint-553 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v26/cmrc1_drcd1_cail1_lic --model_type bert --predict_file train_lic.json --do_eval --overwrite_output_dir --max_seq_length 512 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 8 --threads 12 --model_name chinese-roberta-wwm-ext-large
```



```shell
python test_multi_2.py 
--data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_type bert --predict_file test2_dealed.json --do_eval --overwrite_output_dir --max_seq_length 512 --max_answer_length 40 --per_gpu_eval_batch_size 8 --n_best_size 20 --split_doc --do_lower_case --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v26_2/cmrc1_drcd1_cail1_lic/checkpoint-2209 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v26_2/cmrc1_drcd1_cail1_lic/checkpoint-1657 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v26_2/cmrc1_drcd1_cail1_lic/checkpoint-1105 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v26_2/cmrc1_drcd1_cail1_lic/checkpoint-553 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v26_2/cmrc1_drcd1_cail1_lic
```



### V27

cmrc/drcd/cail/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join_v2 --model_name_or_path /ceph/qbkg/aitingliu/MRC/chinese-roberta-wwm-ext-large --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v27/cmrc --model_type bert --train_file train_cmrc.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 1112 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join_v2 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v27/cmrc/checkpoint-1493 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v27/cmrc1_drcd --model_type bert --train_file train_drcd.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 1112 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join_v2 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v27/cmrc1_drcd/checkpoint-2569 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v27/cmrc1_drcd1_cail --model_type bert --train_file train_cail.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 1112 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join_v2 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v27/cmrc1_drcd1_cail/checkpoint-3874 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v27/cmrc1_drcd1_cail1_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 1112 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join_v2 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v27/cmrc1_drcd1_cail1_lic/checkpoint-1643 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v27/cmrc1_drcd1_cail1_lic --model_type bert --predict_file train_lic.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 1112 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 12 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 1302306029 Apr 30 12:43 checkpoint-1493
drwxr-xr-x 1 mqq mqq 1302306029 Apr 30 14:00 checkpoint-2985

drwxr-xr-x 1 mqq mqq 1302306155 Apr 30 20:28 checkpoint-2569
drwxr-xr-x 1 mqq mqq 1302306155 Apr 30 22:41 checkpoint-5137

drwxr-xr-x 1 mqq mqq 1302306159 May  1 03:51 checkpoint-3874
drwxr-xr-x 1 mqq mqq 1302306159 May  1 07:11 checkpoint-7747

drwxr-xr-x 1 mqq mqq 1302306199 May  1 11:50 checkpoint-1643
drwxr-xr-x 1 mqq mqq 1302306199 May  1 12:32 checkpoint-2464
drwxr-xr-x 1 mqq mqq 1302306199 May  1 13:14 checkpoint-3285
drwxr-xr-x 1 mqq mqq 1302306199 May  1 13:57 checkpoint-4106
drwxr-xr-x 1 mqq mqq 1302306199 May  1 11:07 checkpoint-822

```shell
python test_multi_2.py 
--data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_type bert --predict_file test2_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --max_answer_length 40 --per_gpu_eval_batch_size 8 --n_best_size 20 --split_doc --do_lower_case --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v27/cmrc1_drcd1_cail1_lic/checkpoint-4106 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v27/cmrc1_drcd1_cail1_lic/checkpoint-3285 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v27/cmrc1_drcd1_cail1_lic/checkpoint-2464 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v27/cmrc1_drcd1_cail1_lic/checkpoint-1643 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v27/cmrc1_drcd1_cail1_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v27/cmrc1_drcd1_cail1_lic
```

### V27_2

cmrc/drcd/cail/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join_v2 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v43/webqa_epoch2 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v27_2/cmrc --model_type bert --train_file train_cmrc.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 1112 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v27_2/cmrc
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join_v2 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v27_2/cmrc/checkpoint-1493 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v27_2/cmrc1_drcd --model_type bert --train_file train_drcd.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 1 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 1112 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v27_2/cmrc1_drcd
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join_v2 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v27_2/cmrc1_drcd/checkpoint-2569 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v27_2/cmrc1_drcd1_cail --model_type bert --train_file train_cail.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 1 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 1112 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v27_2/cmrc1_drcd1_cail
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join_v2 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v27_2/cmrc1_drcd1_cail/checkpoint-3874 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v27_2/cmrc1_drcd1_cail1_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 1112 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v27_2/cmrc1_drcd1_cail1_lic
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join_v2 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v27/cmrc1_drcd1_cail1_lic/checkpoint-1643 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v27/cmrc1_drcd1_cail1_lic --model_type bert --predict_file train_lic.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 1112 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 12 --model_name chinese-roberta-wwm-ext-large
```

```shell
python test_multi_2.py 
--data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_type bert --predict_file test2_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --max_answer_length 40 --per_gpu_eval_batch_size 8 --n_best_size 20 --split_doc --do_lower_case --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v27_2/cmrc1_drcd1_cail1_lic/checkpoint-3285 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v27_2/cmrc1_drcd1_cail1_lic/checkpoint-2464 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v27_2/cmrc1_drcd1_cail1_lic/checkpoint-1643 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v27_2/cmrc1_drcd1_cail1_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v27_2/cmrc1_drcd1_cail1_lic
```



### V28

ChineseMRC_V3: cmrc1/drcd/cail/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/keywords_data --model_name_or_path /ceph/qbkg/aitingliu/MRC/chinese-roberta-wwm-ext-large --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v28/cmrc --model_type bert --train_file train_cmrc_kw-tfidf.json --predict_file dev_kw_tfidf.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/keywords_data --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v28/cmrc/checkpoint-1493 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v28/cmrc1_drcd --model_type bert --train_file train_drcd_kw-tfidf.json --predict_file dev_kw_tfidf.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/keywords_data --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v28/cmrc1_drcd/checkpoint-2569 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v28/cmrc1_drcd1_cail --model_type bert --train_file train_cail_kw-tfidf.json --predict_file dev_kw_tfidf.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/keywords_data --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v28/cmrc1_drcd1_cail/checkpoint-3874 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v28/cmrc1_drcd1_cail1_lic --model_type bert --train_file train_kw_tfidf.json --predict_file dev_kw_tfidf.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/keywords_data --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v28/cmrc1_drcd1_cail1_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v28/cmrc1_drcd1_cail1_lic --model_type bert --predict_file train_kw_tfidf.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 12 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 1302314519 May  1 14:52 checkpoint-1493
drwxr-xr-x 1 mqq mqq 1302314519 May  1 16:10 checkpoint-2985

drwxr-xr-x 1 mqq mqq 1302314667 May  1 20:51 checkpoint-2569
drwxr-xr-x 1 mqq mqq 1302314667 May  1 23:04 checkpoint-5137

drwxr-xr-x 1 mqq mqq 1302314693 May  2 19:19 checkpoint-3874
drwxr-xr-x 1 mqq mqq 1302314693 May  2 22:41 checkpoint-7747

drwxr-xr-x 1 mqq mqq 1302314681 May  3 11:36 checkpoint-1643
drwxr-xr-x 1 mqq mqq 1302314681 May  3 12:18 checkpoint-2464
drwxr-xr-x 1 mqq mqq 1302314681 May  3 13:01 checkpoint-3285
drwxr-xr-x 1 mqq mqq 1302314681 May  3 13:43 checkpoint-4106
drwxr-xr-x 1 mqq mqq 1302314681 May  3 10:53 checkpoint-822

```shell
python test_multi_2.py 
--data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/keywords_data --model_type bert --predict_file test2_dealed_kw_tfidf.json --do_eval --overwrite_output_dir --max_seq_length 256 --max_answer_length 40 --per_gpu_eval_batch_size 8 --n_best_size 20 --split_doc --do_lower_case --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v28/cmrc1_drcd1_cail1_lic/checkpoint-4106 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v28/cmrc1_drcd1_cail1_lic/checkpoint-3285 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v28/cmrc1_drcd1_cail1_lic/checkpoint-2464 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v28/cmrc1_drcd1_cail1_lic/checkpoint-1643 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v28/cmrc1_drcd1_cail1_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v28/cmrc1_drcd1_cail1_lic
```

### V28_2

ChineseMRC_V3: cmrc1/drcd/cail/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/keywords_data --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v43/webqa_epoch2 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v28_2/cmrc --model_type bert --train_file train_cmrc_kw-tfidf.json --predict_file dev_kw_tfidf.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/keywords_data --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v28_2/cmrc/checkpoint-1493 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v28_2/cmrc1_drcd --model_type bert --train_file train_drcd_kw-tfidf.json --predict_file dev_kw_tfidf.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 1 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/keywords_data --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v28_2/cmrc1_drcd/checkpoint-2569 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v28_2/cmrc1_drcd1_cail --model_type bert --train_file train_cail_kw-tfidf.json --predict_file dev_kw_tfidf.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 1 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/keywords_data --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v28_2/cmrc1_drcd1_cail/checkpoint-3874 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v28_2/cmrc1_drcd1_cail1_lic --model_type bert --train_file train_kw_tfidf.json --predict_file dev_kw_tfidf.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/keywords_data --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v28/cmrc1_drcd1_cail1_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v28/cmrc1_drcd1_cail1_lic --model_type bert --predict_file train_kw_tfidf.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 12 --model_name chinese-roberta-wwm-ext-large
```

```shell
python test_multi_2.py 
--data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/keywords_data --model_type bert --predict_file test2_dealed_kw_tfidf.json --do_eval --overwrite_output_dir --max_seq_length 256 --max_answer_length 40 --per_gpu_eval_batch_size 8 --n_best_size 20 --split_doc --do_lower_case --threads 12 --output_all_logit --model_name chinese-roberta-wwm-ext-large --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v28_2/cmrc1_drcd1_cail1_lic/checkpoint-3285 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v28_2/cmrc1_drcd1_cail1_lic/checkpoint-2464 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v28_2/cmrc1_drcd1_cail1_lic/checkpoint-1643 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v28_2/cmrc1_drcd1_cail1_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v28_2/cmrc1_drcd1_cail1_lic
```



### V29

baidushort/cetc1500/cmrc/drcd/cail/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/chinese-roberta-wwm-ext-large --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29/baidushort --model_type bert --train_file train_baidushort.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29/baidushort/checkpoint-6491 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29/baidushort1_cetc1500 --model_type bert --train_file train_cetc1500.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29/baidushort1_cetc1500/checkpoint-15595 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29/baidushort1_cetc15002_cmrc --model_type bert --train_file train_cmrc.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29/baidushort1_cetc15002_cmrc/checkpoint-1493 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29/baidushort1_cetc15002_cmrc1_drcd --model_type bert --train_file train_drcd.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29/baidushort1_cetc15002_cmrc1_drcd/checkpoint-2569 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29/baidushort1_cetc15002_cmrc1_drcd1_cail --model_type bert --train_file train_cail.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29/baidushort1_cetc15002_cmrc1_drcd1_cail/checkpoint-3874 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29/baidushort1_cetc15002_cmrc1_drcd1_cail1_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29/baidushort1_cetc15002_cmrc1_drcd1_cail1_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29/baidushort1_cetc15002_cmrc1_drcd1_cail1_lic --model_type bert --predict_file train_lic.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 1302306054 May  2 01:06 checkpoint-12981
drwxr-xr-x 1 mqq mqq 1302306054 May  1 19:30 checkpoint-6491

drwxr-xr-x 1 mqq mqq 1302306216 May  2 22:28 checkpoint-15595
drwxr-xr-x 1 mqq mqq 1302306216 May  2 15:46 checkpoint-7798

drwxr-xr-x 1 mqq mqq 1302306215 May  3 11:48 checkpoint-1493
drwxr-xr-x 1 mqq mqq 1302306215 May  3 13:05 checkpoint-2985

drwxr-xr-x 1 mqq mqq 1302306224 May  3 21:00 checkpoint-2569
drwxr-xr-x 1 mqq mqq 1302306224 May  3 23:13 checkpoint-5137

drwxr-xr-x 1 mqq mqq 1302306236 May  4 11:55 checkpoint-3874
drwxr-xr-x 1 mqq mqq 1302306236 May  4 15:15 checkpoint-7747

drwxr-xr-x 1 mqq mqq 1302306250 May  4 18:03 checkpoint-1643
drwxr-xr-x 1 mqq mqq 1302306250 May  4 18:45 checkpoint-2464
drwxr-xr-x 1 mqq mqq 1302306250 May  4 19:27 checkpoint-3285
drwxr-xr-x 1 mqq mqq 1302306250 May  4 20:09 checkpoint-4106
drwxr-xr-x 1 mqq mqq 1302306250 May  4 17:20 checkpoint-822

```shell
python test_multi_2.py 
--data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_type bert --predict_file test2_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --max_answer_length 40 --per_gpu_eval_batch_size 8 --n_best_size 20 --split_doc --do_lower_case --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29/baidushort1_cetc15002_cmrc1_drcd1_cail1_lic/checkpoint-4106 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29/baidushort1_cetc15002_cmrc1_drcd1_cail1_lic/checkpoint-3285 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29/baidushort1_cetc15002_cmrc1_drcd1_cail1_lic/checkpoint-2464 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29/baidushort1_cetc15002_cmrc1_drcd1_cail1_lic/checkpoint-1643 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29/baidushort1_cetc15002_cmrc1_drcd1_cail1_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29/baidushort1_cetc15002_cmrc1_drcd1_cail1_lic
```

### V29_2

baidushort/cetc1500/cmrc/drcd/cail/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v14_2/baidushort/checkpoint-6491 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29_2/baidushort1_cetc1500 --model_type bert --train_file train_cetc1500.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 1 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29_2/baidushort1_cetc1500
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29_2/baidushort1_cetc1500/checkpoint-7798 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29_2/baidushort1_cetc15001_cmrc --model_type bert --train_file train_cmrc.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 1 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29_2/baidushort1_cetc15001_cmrc
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29_2/baidushort1_cetc15001_cmrc/checkpoint-1493 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29_2/baidushort1_cetc15001_cmrc1_drcd --model_type bert --train_file train_drcd.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 1 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29_2/baidushort1_cetc15001_cmrc1_drcd
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29_2/baidushort1_cetc15001_cmrc1_drcd/checkpoint-2569 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29_2/baidushort1_cetc15001_cmrc1_drcd1_cail --model_type bert --train_file train_cail.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 1 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29_2/baidushort1_cetc15001_cmrc1_drcd1_cail
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29_2/baidushort1_cetc15001_cmrc1_drcd1_cail/checkpoint-3874 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29_2/baidushort1_cetc15001_cmrc1_drcd1_cail1_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29_2/baidushort1_cetc15001_cmrc1_drcd1_cail1_lic
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29/baidushort1_cetc15001_cmrc1_drcd1_cail1_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29/baidushort1_cetc15001_cmrc1_drcd1_cail1_lic --model_type bert --predict_file train_lic.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python test_multi_2.py 
--data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_type bert --predict_file test2_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --max_answer_length 40 --per_gpu_eval_batch_size 8 --n_best_size 20 --split_doc --do_lower_case --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29_2/baidushort1_cetc15001_cmrc1_drcd1_cail1_lic/checkpoint-3285 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29_2/baidushort1_cetc15001_cmrc1_drcd1_cail1_lic/checkpoint-4106 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29_2/baidushort1_cetc15001_cmrc1_drcd1_cail1_lic/checkpoint-2464 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29_2/baidushort1_cetc15001_cmrc1_drcd1_cail1_lic/checkpoint-1643 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29_2/baidushort1_cetc15001_cmrc1_drcd1_cail1_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v29_2/baidushort1_cetc15001_cmrc1_drcd1_cail1_lic
```



### V30

lic_extended_v5/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/chinese-roberta-wwm-ext-large --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v30/lic_extended_v5 --model_type bert --train_file train_extended_v5.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v30/lic_extended_v5/checkpoint-1465 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v30/lic_extended_v5_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v30/lic_extended_v5_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v30/lic_extended_v5_lic --model_type bert --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 1302306068 May  3 21:18 checkpoint-1465
drwxr-xr-x 1 mqq mqq 1302306068 May  3 20:40 checkpoint-733

drwxr-xr-x 1 mqq mqq 1302306195 May  3 22:53 checkpoint-1643
drwxr-xr-x 1 mqq mqq 1302306195 May  3 23:36 checkpoint-2464
drwxr-xr-x 1 mqq mqq 1302306195 May  4 00:18 checkpoint-3285
drwxr-xr-x 1 mqq mqq 1302306195 May  4 01:00 checkpoint-4106
drwxr-xr-x 1 mqq mqq 1302306195 May  3 22:11 checkpoint-822

### V31

lic_extended_v6

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v31/lic_extended_v6/checkpoint-3107 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v31/lic_extended_v6 --model_type bert --train_file train_extended_v6.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 12 --model_name chinese-roberta-wwm-ext-large --inherit_global_step
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v31/lic_extended_v6/checkpoint-1554 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v31/lic_extended_v6 --model_type bert --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 1302306062 May  3 21:21 checkpoint-1554
drwxr-xr-x 1 mqq mqq 1302306062 May  3 22:41 checkpoint-3107
drwxr-xr-x 1 mqq mqq 1302306185 May  4 00:14 checkpoint-4660
drwxr-xr-x 1 mqq mqq 1302306185 May  4 01:34 checkpoint-6213
drwxr-xr-x 1 mqq mqq 1302306185 May  4 02:54 checkpoint-7766

### V32

cmrc1/drcd/cail/lic_extend_template_v2

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23/cmrc1_drcd1_cail/checkpoint-3874 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v32/cmrc1_drcd1_cail1_lic --model_type bert --train_file train_extend_template_v2.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v32/cmrc1_drcd1_cail1_lic/checkpoint-9205 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v32/cmrc1_drcd1_cail1_lic --model_type bert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit
```

drwxr-xr-x 1 mqq mqq 1302306207 May  5 22:40 checkpoint-11506
drwxr-xr-x 1 mqq mqq 1302306207 May  5 14:47 checkpoint-2302
drwxr-xr-x 1 mqq mqq 1302306207 May  5 16:45 checkpoint-4603
drwxr-xr-x 1 mqq mqq 1302306207 May  5 18:44 checkpoint-6904
drwxr-xr-x 1 mqq mqq 1302306207 May  5 20:42 checkpoint-9205

### V33

cmrc1/drcd/cail/lic_extended_v6

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23/cmrc1_drcd1_cail/checkpoint-3874 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v33/cmrc1_drcd1_cail1_lic --model_type bert --train_file train_extended_v6.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v33/cmrc1_drcd1_cail1_lic/checkpoint-1554 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v33/cmrc1_drcd1_cail1_lic --model_type bert --predict_file train_lic.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 12 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 1302306198 May  4 17:53 checkpoint-1554
drwxr-xr-x 1 mqq mqq 1302306198 May  4 19:13 checkpoint-3107
drwxr-xr-x 1 mqq mqq 1302306198 May  4 20:33 checkpoint-4660
drwxr-xr-x 1 mqq mqq 1302306198 May  4 21:53 checkpoint-6213
drwxr-xr-x 1 mqq mqq 1302306198 May  4 23:13 checkpoint-7766

```shell
python test_multi_2.py 
--data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_type bert --predict_file test2_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --max_answer_length 40 --per_gpu_eval_batch_size 8 --n_best_size 20 --split_doc --do_lower_case --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v33/cmrc1_drcd1_cail1_lic/checkpoint-7766 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v33/cmrc1_drcd1_cail1_lic/checkpoint-6213 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v33/cmrc1_drcd1_cail1_lic/checkpoint-4660 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v33/cmrc1_drcd1_cail1_lic/checkpoint-3107 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v33/cmrc1_drcd1_cail1_lic/checkpoint-1554 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v33/cmrc1_drcd1_cail1_lic
```

### V33_2

cmrc1/drcd/cail/lic_extended_v6

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23_2/cmrc1_drcd1_cail/checkpoint-3874 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v33_2/cmrc1_drcd1_cail1_lic --model_type bert --train_file train_extended_v6.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v33_2/cmrc1_drcd1_cail1_lic
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v33/cmrc1_drcd1_cail1_lic/checkpoint-1554 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v33/cmrc1_drcd1_cail1_lic --model_type bert --predict_file train_lic.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 12 --model_name chinese-roberta-wwm-ext-large
```



```shell
python test_multi_2.py 
--data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_type bert --predict_file test2_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --max_answer_length 40 --per_gpu_eval_batch_size 8 --n_best_size 20 --split_doc --do_lower_case --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v33_2/cmrc1_drcd1_cail1_lic/checkpoint-6213 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v33_2/cmrc1_drcd1_cail1_lic/checkpoint-4660 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v33_2/cmrc1_drcd1_cail1_lic/checkpoint-3107 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v33_2/cmrc1_drcd1_cail1_lic/checkpoint-1554 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v33_2/cmrc1_drcd1_cail1_lic
```



### V34

预训练模型baidushort_dureader_lic_epoch_2：cmrc1/drcd/cail/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v34/baidushort_dureader_lic_epoch_2 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v34/cmrc --model_type bert --train_file train_cmrc.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v34/cmrc/checkpoint-1493 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v34/cmrc1_drcd --model_type bert --train_file train_drcd.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v34/cmrc1_drcd/checkpoint-5137 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v34/cmrc1_drcd2_cail --model_type bert --train_file train_cail.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v34/cmrc1_drcd2_cail/checkpoint-3874 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v34/cmrc1_drcd2_cail1_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v34/cmrc1_drcd2_cail1_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v34/cmrc1_drcd2_cail1_lic --model_type bert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit
```

drwxr-xr-x 1 mqq mqq 1302306202 May  7 01:41 checkpoint-1493
drwxr-xr-x 1 mqq mqq 1302306202 May  7 02:58 checkpoint-2985

drwxr-xr-x 1 mqq mqq 1302306199 May  7 12:08 checkpoint-2569
drwxr-xr-x 1 mqq mqq 1302306199 May  7 14:21 checkpoint-5137

drwxr-xr-x 1 mqq mqq 1302306221 May  7 19:45 checkpoint-3874
drwxr-xr-x 1 mqq mqq 1302306221 May  7 23:05 checkpoint-7747

drwxr-xr-x 1 mqq mqq 1302306221 May  8 00:53 checkpoint-1643
drwxr-xr-x 1 mqq mqq 1302306221 May  8 01:35 checkpoint-2464
drwxr-xr-x 1 mqq mqq 1302306221 May  8 02:17 checkpoint-3285
drwxr-xr-x 1 mqq mqq 1302306221 May  8 03:00 checkpoint-4106
drwxr-xr-x 1 mqq mqq 1302306221 May  8 00:10 checkpoint-822

```shell
python test_multi_2.py 
--data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_type bert --predict_file test2_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --max_answer_length 40 --per_gpu_eval_batch_size 8 --n_best_size 20 --split_doc --do_lower_case --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v34/cmrc1_drcd2_cail1_lic/checkpoint-4106 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v34/cmrc1_drcd2_cail1_lic/checkpoint-3285 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v34/cmrc1_drcd2_cail1_lic/checkpoint-2464 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v34/cmrc1_drcd2_cail1_lic/checkpoint-1643 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v34/cmrc1_drcd2_cail1_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v34/cmrc1_drcd2_cail1_lic
```



### V35

cmrc1/drcd/cail/lic_extend_template_v1/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23/cmrc1_drcd1_cail/checkpoint-3874 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v35/cmrc1_drcd1_cail1_lic_template_v1 --model_type bert --train_file train_extend_template_v1.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v35/cmrc1_drcd1_cail1_lic_template_v1/checkpoint-1481 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v35/cmrc1_drcd1_cail1_lic_template_v1_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v35/cmrc1_drcd1_cail1_lic_template_v1_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v35/cmrc1_drcd1_cail1_lic_template_v1_lic --model_type bert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit
```

drwxr-xr-x 1 mqq mqq 1302306229 May  7 10:03 checkpoint-1481
drwxr-xr-x 1 mqq mqq 1302306229 May  7 11:20 checkpoint-2961

drwxr-xr-x 1 mqq mqq 1302306233 May  7 13:28 checkpoint-1643
drwxr-xr-x 1 mqq mqq 1302306233 May  7 14:10 checkpoint-2464
drwxr-xr-x 1 mqq mqq 1302306233 May  7 14:53 checkpoint-3285
drwxr-xr-x 1 mqq mqq 1302306233 May  7 15:35 checkpoint-4106
drwxr-xr-x 1 mqq mqq 1302306233 May  7 12:45 checkpoint-822

```shell
python test_multi_2.py 
--data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_type bert --predict_file test2_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --max_answer_length 40 --per_gpu_eval_batch_size 8 --n_best_size 20 --split_doc --do_lower_case --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v35/cmrc1_drcd1_cail1_lic_template_v1_lic/checkpoint-4106 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v35/cmrc1_drcd1_cail1_lic_template_v1_lic/checkpoint-3285 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v35/cmrc1_drcd1_cail1_lic_template_v1_lic/checkpoint-2464 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v35/cmrc1_drcd1_cail1_lic_template_v1_lic/checkpoint-1643 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v35/cmrc1_drcd1_cail1_lic_template_v1_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v35/cmrc1_drcd1_cail1_lic_template_v1_lic
```

### V35_2

cmrc1/drcd/cail/lic_extend_template_v1/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23_2/cmrc1_drcd1_cail/checkpoint-3874 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v35_2/cmrc1_drcd1_cail1_lic_template_v1 --model_type bert --train_file train_extend_template_v1.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 1 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v35_2/cmrc1_drcd1_cail1_lic_template_v1
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v35_2/cmrc1_drcd1_cail1_lic_template_v1/checkpoint-1481 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v35_2/cmrc1_drcd1_cail1_lic_template_v1_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v35_2/cmrc1_drcd1_cail1_lic_template_v1_lic
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v35/cmrc1_drcd1_cail1_lic_template_v1_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v35/cmrc1_drcd1_cail1_lic_template_v1_lic --model_type bert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit
```

```shell
python test_multi_2.py 
--data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_type bert --predict_file test2_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --max_answer_length 40 --per_gpu_eval_batch_size 8 --n_best_size 20 --split_doc --do_lower_case --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v35_2/cmrc1_drcd1_cail1_lic_template_v1_lic/checkpoint-3285 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v35_2/cmrc1_drcd1_cail1_lic_template_v1_lic/checkpoint-2464 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v35_2/cmrc1_drcd1_cail1_lic_template_v1_lic/checkpoint-1643 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v35_2/cmrc1_drcd1_cail1_lic_template_v1_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v35_2/cmrc1_drcd1_cail1_lic_template_v1_lic
```

--model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v35_2/cmrc1_drcd1_cail1_lic_template_v1_lic/checkpoint-4106

### V36

cmrc1/drcd/cail/lic_extended_v5/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23/cmrc1_drcd1_cail/checkpoint-3874 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v36/cmrc1_drcd1_cail1_lic_extended_v5 --model_type bert --train_file train_extended_v5.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v36/cmrc1_drcd1_cail1_lic_extended_v5/checkpoint-733 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v36/cmrc1_drcd1_cail1_lic_extended_v5_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v36/cmrc1_drcd1_cail1_lic_extended_v5_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v36/cmrc1_drcd1_cail1_lic_extended_v5_lic --model_type bert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit
```

drwxr-xr-x 1 mqq mqq 1302306212 May  7 09:52 checkpoint-1465
drwxr-xr-x 1 mqq mqq 1302306212 May  7 09:14 checkpoint-733

drwxr-xr-x 1 mqq mqq 1302306240 May  7 13:00 checkpoint-1643
drwxr-xr-x 1 mqq mqq 1302306240 May  7 13:42 checkpoint-2464
drwxr-xr-x 1 mqq mqq 1302306240 May  7 14:25 checkpoint-3285
drwxr-xr-x 1 mqq mqq 1302306240 May  7 15:07 checkpoint-4106
drwxr-xr-x 1 mqq mqq 1302306240 May  7 12:17 checkpoint-822

```shell
python test_multi_2.py 
--data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_type bert --predict_file test2_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --max_answer_length 40 --per_gpu_eval_batch_size 8 --n_best_size 20 --split_doc --do_lower_case --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v36/cmrc1_drcd1_cail1_lic_extended_v5_lic/checkpoint-4106 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v36/cmrc1_drcd1_cail1_lic_extended_v5_lic/checkpoint-3285 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v36/cmrc1_drcd1_cail1_lic_extended_v5_lic/checkpoint-2464 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v36/cmrc1_drcd1_cail1_lic_extended_v5_lic/checkpoint-1643 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v36/cmrc1_drcd1_cail1_lic_extended_v5_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v36/cmrc1_drcd1_cail1_lic_extended_v5_lic
```

### V36_2

cmrc1/drcd/cail/lic_extended_v5/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v23_2/cmrc1_drcd1_cail/checkpoint-3874 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v36_2/cmrc1_drcd1_cail1_lic_extended_v5 --model_type bert --train_file train_extended_v5.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 1 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v36_2/cmrc1_drcd1_cail1_lic_extended_v5
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v36_2/cmrc1_drcd1_cail1_lic_extended_v5/checkpoint-733 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v36_2/cmrc1_drcd1_cail1_lic_extended_v5_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v36_2/cmrc1_drcd1_cail1_lic_extended_v5_lic
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v36/cmrc1_drcd1_cail1_lic_extended_v5_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v36/cmrc1_drcd1_cail1_lic_extended_v5_lic --model_type bert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit
```

```shell
python test_multi_2.py 
--data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_type bert --predict_file test2_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --max_answer_length 40 --per_gpu_eval_batch_size 8 --n_best_size 20 --split_doc --do_lower_case --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v36_2/cmrc1_drcd1_cail1_lic_extended_v5_lic/checkpoint-3285 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v36_2/cmrc1_drcd1_cail1_lic_extended_v5_lic/checkpoint-2464 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v36_2/cmrc1_drcd1_cail1_lic_extended_v5_lic/checkpoint-1643 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v36_2/cmrc1_drcd1_cail1_lic_extended_v5_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v36_2/cmrc1_drcd1_cail1_lic_extended_v5_lic
```

 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v36_2/cmrc1_drcd1_cail1_lic_extended_v5_lic/checkpoint-4106

### V37

cmrc1/drcd/cail/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/chinese-roberta-wwm-ext-large --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v37/cmrc --model_type bert --train_file train_cmrc.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 16 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v37/cmrc/checkpoint-374 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v37/cmrc1_drcd --model_type bert --train_file train_drcd.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 16 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v37/cmrc1_drcd/checkpoint-643 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v37/cmrc1_drcd1_cail --model_type bert --train_file train_cail.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 16 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v37/cmrc1_drcd1_cail/checkpoint-969 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v37/cmrc1_drcd1_cail1_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 16 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v37/cmrc1_drcd1_cail1_lic/checkpoint-411 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v37/cmrc1_drcd1_cail1_lic --model_type bert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 16 --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit
```

drwxr-xr-x 1 mqq mqq 1302306046 May  7 10:15 checkpoint-374
drwxr-xr-x 1 mqq mqq 1302306046 May  7 11:29 checkpoint-747

drwxr-xr-x 1 mqq mqq 1302306171 May  7 16:28 checkpoint-1285
drwxr-xr-x 1 mqq mqq 1302306171 May  7 14:20 checkpoint-643

drwxr-xr-x 1 mqq mqq 1302306187 May  7 23:13 checkpoint-1937
drwxr-xr-x 1 mqq mqq 1302306187 May  7 20:01 checkpoint-969

drwxr-xr-x 1 mqq mqq 1302306201 May  8 02:55 checkpoint-1026
drwxr-xr-x 1 mqq mqq 1302306201 May  8 00:12 checkpoint-206
drwxr-xr-x 1 mqq mqq 1302306201 May  8 00:53 checkpoint-411
drwxr-xr-x 1 mqq mqq 1302306201 May  8 01:33 checkpoint-616
drwxr-xr-x 1 mqq mqq 1302306201 May  8 02:14 checkpoint-821

```shell
python test_multi_2.py 
--data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_type bert --predict_file test2_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --max_answer_length 40 --per_gpu_eval_batch_size 8 --n_best_size 20 --split_doc --do_lower_case --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v37/cmrc1_drcd1_cail1_lic/checkpoint-1026 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v37/cmrc1_drcd1_cail1_lic/checkpoint-821 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v37/cmrc1_drcd1_cail1_lic/checkpoint-616 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v37/cmrc1_drcd1_cail1_lic/checkpoint-411 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v37/cmrc1_drcd1_cail1_lic/checkpoint-206 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v37/cmrc1_drcd1_cail1_lic
```

### V37_2

cmrc1/drcd/cail/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v43/webqa_epoch2 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v37_2/cmrc --model_type bert --train_file train_cmrc.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 16 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v37_2/cmrc
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v37_2/cmrc/checkpoint-374 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v37_2/cmrc1_drcd --model_type bert --train_file train_drcd.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 1 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 16 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v37_2/cmrc1_drcd
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v37_2/cmrc1_drcd/checkpoint-643 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v37_2/cmrc1_drcd1_cail --model_type bert --train_file train_cail.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 16 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v37_2/cmrc1_drcd1_cail
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v37_2/cmrc1_drcd1_cail/checkpoint-969 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v37_2/cmrc1_drcd1_cail1_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 16 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v37_2/cmrc1_drcd1_cail1_lic
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v37/cmrc1_drcd1_cail1_lic/checkpoint-411 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v37/cmrc1_drcd1_cail1_lic --model_type bert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 16 --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit
```

```shell
python test_multi_2.py 
--data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_type bert --predict_file test2_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --max_answer_length 40 --per_gpu_eval_batch_size 8 --n_best_size 20 --split_doc --do_lower_case --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v37_2/cmrc1_drcd1_cail1_lic/checkpoint-821 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v37_2/cmrc1_drcd1_cail1_lic/checkpoint-616 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v37_2/cmrc1_drcd1_cail1_lic/checkpoint-411 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v37_2/cmrc1_drcd1_cail1_lic/checkpoint-206 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v37_2/cmrc1_drcd1_cail1_lic
```

--model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v37_2/cmrc1_drcd1_cail1_lic/checkpoint-1026 

### V38

预训练模型baidu_atec_zybang_epoch2：cmrc/drcd/cail/zybang/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v38/baidu_atec_zybang_epoch2 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v38/cmrc --model_type bert --train_file train_cmrc.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 16 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v38/cmrc/checkpoint-374 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v38/cmrc1_drcd --model_type bert --train_file train_drcd.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 16 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v38/cmrc1_drcd/checkpoint-643 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v38/cmrc1_drcd1_cail --model_type bert --train_file train_cail.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 16 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v38/cmrc1_drcd1_cail/checkpoint-969 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v38/cmrc1_drcd1_cail1_zybang --model_type bert --train_file train_zybang.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 16 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v38/cmrc1_drcd1_cail1_zybang/checkpoint-75 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v38/cmrc1_drcd1_cail1_zybang2_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 16 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v38/cmrc1_drcd1_cail1_zybang2_lic/checkpoint-206 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v38/cmrc1_drcd1_cail1_zybang2_lic --model_type bert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 16 --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit
```

drwxr-xr-x 1 mqq mqq 1302306203 May  8 14:35 checkpoint-374
drwxr-xr-x 1 mqq mqq 1302306203 May  8 15:49 checkpoint-747

drwxr-xr-x 1 mqq mqq 1302306212 May  8 21:51 checkpoint-1285
drwxr-xr-x 1 mqq mqq 1302306212 May  8 19:44 checkpoint-643

drwxr-xr-x 1 mqq mqq 1302306220 May  9 06:30 checkpoint-1937
drwxr-xr-x 1 mqq mqq 1302306220 May  9 03:18 checkpoint-969

drwxr-xr-x 1 mqq mqq 1302306248 May  9 08:17 checkpoint-112
drwxr-xr-x 1 mqq mqq 1302306248 May  9 08:25 checkpoint-149
drwxr-xr-x 1 mqq mqq 1302306248 May  9 08:32 checkpoint-186
drwxr-xr-x 1 mqq mqq 1302306248 May  9 08:03 checkpoint-38
drwxr-xr-x 1 mqq mqq 1302306248 May  9 08:10 checkpoint-75

drwxr-xr-x 1 mqq mqq 1302306245 May  9 15:23 checkpoint-1026
drwxr-xr-x 1 mqq mqq 1302306245 May  9 12:40 checkpoint-206
drwxr-xr-x 1 mqq mqq 1302306245 May  9 13:21 checkpoint-411
drwxr-xr-x 1 mqq mqq 1302306245 May  9 14:02 checkpoint-616
drwxr-xr-x 1 mqq mqq 1302306245 May  9 14:42 checkpoint-821

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v38/cmrc1_drcd1_cail/checkpoint-969 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v38/cmrc1_drcd1_cail1_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 16 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v38/cmrc1_drcd1_cail1_lic
```

drwxr-xr-x 1 mqq mqq 1302306336 May 16 13:34 checkpoint-1026
drwxr-xr-x 1 mqq mqq 1327341949 May 16 14:51 checkpoint-206
drwxr-xr-x 1 mqq mqq 1327314172 May 16 14:50 checkpoint-411
drwxr-xr-x 1 mqq mqq 1327227413 May 16 14:50 checkpoint-616
drwxr-xr-x 1 mqq mqq 1327369681 May 16 14:49 checkpoint-821

```shell
python test_multi_2.py 
--data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_type bert --predict_file test2_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --max_answer_length 40 --per_gpu_eval_batch_size 8 --n_best_size 20 --split_doc --do_lower_case --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v38/cmrc1_drcd1_cail1_lic/checkpoint-616 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v38/cmrc1_drcd1_cail1_lic/checkpoint-411 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v38/cmrc1_drcd1_cail1_lic/checkpoint-206 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v38/cmrc1_drcd1_cail1_lic/checkpoint-821 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v38/cmrc1_drcd1_cail1_lic/checkpoint-1026 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v38/cmrc1_drcd1_cail1_lic
```



### V39

预训练模型baidu_atec_zybang_dev_test1_epoch2：cmrc/drcd/cail/zybang/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v39/baidu_atec_zybang_dev_test1_epoch2 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v39/cmrc --model_type bert --train_file train_cmrc.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 16 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v39/cmrc/checkpoint-374 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v39/cmrc1_drcd --model_type bert --train_file train_drcd.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 16 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v39/cmrc1_drcd/checkpoint-1285 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v39/cmrc1_drcd2_cail --model_type bert --train_file train_cail.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 16 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v39/cmrc1_drcd2_cail/checkpoint-969 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v39/cmrc1_drcd2_cail1_zybang --model_type bert --train_file train_zybang.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 16 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v39/cmrc1_drcd2_cail1_zybang/checkpoint-75 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v39/cmrc1_drcd2_cail1_zybang2_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 16 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v39/cmrc1_drcd2_cail1_lic/checkpoint-616 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v39/cmrc1_drcd2_cail1_lic --model_type bert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 20 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 16 --threads 12 --model_name chinese-roberta-wwm-ext-large --max_answer_length 40
```

drwxr-xr-x 1 mqq mqq 1302306215 May  9 01:28 checkpoint-374
drwxr-xr-x 1 mqq mqq 1302306215 May  9 02:42 checkpoint-747

drwxr-xr-x 1 mqq mqq 1302306202 May  9 12:07 checkpoint-1285
drwxr-xr-x 1 mqq mqq 1302306202 May  9 10:00 checkpoint-643

drwxr-xr-x 1 mqq mqq 1302306207 May  9 19:25 checkpoint-1937
drwxr-xr-x 1 mqq mqq 1302306207 May  9 16:13 checkpoint-969

drwxr-xr-x 1 mqq mqq 1302306222 May  9 21:27 checkpoint-38
drwxr-xr-x 1 mqq mqq 1302306222 May  9 21:34 checkpoint-75

drwxr-xr-x 1 mqq mqq 1302306243 May 10 02:55 checkpoint-1026
drwxr-xr-x 1 mqq mqq 1302306243 May 10 00:12 checkpoint-206
drwxr-xr-x 1 mqq mqq 1302306243 May 10 00:53 checkpoint-411
drwxr-xr-x 1 mqq mqq 1302306243 May 10 01:33 checkpoint-616
drwxr-xr-x 1 mqq mqq 1302306243 May 10 02:14 checkpoint-821

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v39/cmrc1_drcd2_cail/checkpoint-969 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v39/cmrc1_drcd2_cail1_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 16 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v39/cmrc1_drcd2_cail1_lic
```

drwxr-xr-x 1 mqq mqq 1302306318 May 16 13:34 checkpoint-1026
drwxr-xr-x 1 mqq mqq 1302306318 May 16 10:51 checkpoint-206
drwxr-xr-x 1 mqq mqq 1302306318 May 16 11:31 checkpoint-411
drwxr-xr-x 1 mqq mqq 1302306318 May 16 12:12 checkpoint-616
drwxr-xr-x 1 mqq mqq 1302306318 May 16 12:53 checkpoint-821

```shell
python test_multi_2.py 
--data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_type bert --predict_file test2_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --max_answer_length 40 --per_gpu_eval_batch_size 8 --n_best_size 20 --split_doc --do_lower_case --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v39/cmrc1_drcd2_cail1_lic/checkpoint-616 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v39/cmrc1_drcd2_cail1_lic/checkpoint-206 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v39/cmrc1_drcd2_cail1_lic/checkpoint-411 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v39/cmrc1_drcd2_cail1_lic/checkpoint-821 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v39/cmrc1_drcd2_cail1_lic/checkpoint-1026 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v39/cmrc1_drcd2_cail1_lic
```



### V40

预训练模型baidu_atec_zybang_dev_test1_epoch2：cmrc/drcd/cail/zybang/lic_extended_v5/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v39/cmrc1_drcd2_cail1_zybang/checkpoint-75 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v40/cmrc1_drcd2_cail1_zybang2_lic_extended_v5 --model_type bert --train_file train_extended_v5.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 16 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v40/cmrc1_drcd2_cail1_zybang2_lic_extended_v5/checkpoint-184 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v40/cmrc1_drcd2_cail1_zybang2_lic_extended_v5_lic --model_type bert --train_file train_lic_all.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 16 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_all_logit
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v40/cmrc1_drcd2_cail1_lic_extended_v5/checkpoint-184 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v40/cmrc1_drcd2_cail1_lic_extended_v5 --model_type bert --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 16 --threads 12 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v40/cmrc1_drcd2_cail1_lic_extended_v5
```

drwxr-xr-x 1 mqq mqq 1302306255 May 10 16:25 checkpoint-184
drwxr-xr-x 1 mqq mqq 1302306255 May 10 17:01 checkpoint-367

drwxr-xr-x 1 mqq mqq 1302306273 May 10 21:12 checkpoint-1061
drwxr-xr-x 1 mqq mqq 1302306273 May 10 18:24 checkpoint-213
drwxr-xr-x 1 mqq mqq 1302306273 May 10 19:06 checkpoint-425
drwxr-xr-x 1 mqq mqq 1302306273 May 10 19:48 checkpoint-637
drwxr-xr-x 1 mqq mqq 1302306273 May 10 20:30 checkpoint-849

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v39/cmrc1_drcd2_cail/checkpoint-969 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v40/cmrc1_drcd2_cail1_lic_extended_v5 --model_type bert --train_file train_extended_v5.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 16 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v40/cmrc1_drcd2_cail1_lic_extended_v5
```

drwxr-xr-x 1 mqq mqq 1302306346 May 16 10:49 checkpoint-184
drwxr-xr-x 1 mqq mqq 1302306346 May 16 11:26 checkpoint-367

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v40/cmrc1_drcd2_cail1_lic_extended_v5/checkpoint-184 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v40/cmrc1_drcd2_cail1_lic_extended_v5_lic --model_type bert --train_file train_lic_all.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 16 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v40/cmrc1_drcd2_cail1_lic_extended_v5_lic
```

drwxr-xr-x 1 mqq mqq 1302306385 May 16 17:02 checkpoint-1061
drwxr-xr-x 1 mqq mqq 1302306385 May 16 14:13 checkpoint-213
drwxr-xr-x 1 mqq mqq 1302306385 May 16 14:55 checkpoint-425
drwxr-xr-x 1 mqq mqq 1302306385 May 16 15:37 checkpoint-637
drwxr-xr-x 1 mqq mqq 1302306385 May 16 16:20 checkpoint-849

```shell
python test_multi_2.py 
--data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_type bert --predict_file test2_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --max_answer_length 40 --per_gpu_eval_batch_size 8 --n_best_size 20 --split_doc --do_lower_case --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v40/cmrc1_drcd2_cail1_lic_extended_v5_lic/checkpoint-1061 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v40/cmrc1_drcd2_cail1_lic_extended_v5_lic/checkpoint-849 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v40/cmrc1_drcd2_cail1_lic_extended_v5_lic/checkpoint-637 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v40/cmrc1_drcd2_cail1_lic_extended_v5_lic/checkpoint-425 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v40/cmrc1_drcd2_cail1_lic_extended_v5_lic/checkpoint-213 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v40/cmrc1_drcd2_cail1_lic_extended_v5_lic
```

### V41

webqa/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/chinese-roberta-wwm-ext-large --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v41/webqa --model_type bert --train_file train_webqa.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 12 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v41/webqa
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v41/webqa/checkpoint-10869 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v41/webqa2_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v41/webqa2_lic
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v41/webqa2_lic/checkpoint-4106 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v41/webqa2_lic --model_type bert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v41/webqa2_lic
```

drwxr-xr-x 1 mqq mqq 1302306134 May 15 08:35 checkpoint-10869
drwxr-xr-x 1 mqq mqq 1302306134 May 15 03:55 checkpoint-5435

drwxr-xr-x 1 mqq mqq 1302306280 May 15 13:11 checkpoint-1643
drwxr-xr-x 1 mqq mqq 1302306280 May 15 13:53 checkpoint-2464
drwxr-xr-x 1 mqq mqq 1302306280 May 15 14:35 checkpoint-3285
drwxr-xr-x 1 mqq mqq 1302306280 May 15 15:18 checkpoint-4106
drwxr-xr-x 1 mqq mqq 1302306280 May 15 12:28 checkpoint-822



### V42

zybang/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/chinese-roberta-wwm-ext-large --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v42/zybang --model_type bert --train_file train_zybang.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 12 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v42/zybang
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v42/zybang/checkpoint-149 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v42/zybang1_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v42/zybang1_lic
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v42/zybang1_lic/checkpoint-3285 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v42/zybang1_lic --model_type bert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v42/zybang1_lic
```

drwxr-xr-x 1 mqq mqq 1302306133 May 15 13:05 checkpoint-149
drwxr-xr-x 1 mqq mqq 1302306133 May 15 13:12 checkpoint-297

drwxr-xr-x 1 mqq mqq 1327302081 May 15 17:20 checkpoint-1643
drwxr-xr-x 1 mqq mqq 1327275253 May 15 17:22 checkpoint-2464
drwxr-xr-x 1 mqq mqq 1327662577 May 15 17:24 checkpoint-3285
drwxr-xr-x 1 mqq mqq 1302306277 May 15 17:37 checkpoint-4106
drwxr-xr-x 1 mqq mqq 1327459305 May 15 17:18 checkpoint-822

```shell
python test_multi_2.py 
--data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_type bert --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --max_answer_length 30 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --do_lower_case --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v42/zybang1_lic/checkpoint-822 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v42/zybang1_lic/checkpoint-1643 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v42/zybang1_lic/checkpoint-2464 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v42/zybang1_lic/checkpoint-3285 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v42/zybang1_lic
```

### V43

webqa1/cmrc1/drcd/cail/lic

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v43/webqa_epoch2 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v43/webqa --model_type bert --train_file train_webqa.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v43/webqa
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v43/webqa/checkpoint-5435 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v43/webqa1_cmrc --model_type bert --train_file train_cmrc.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v43/webqa1_cmrc
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v43/webqa1_cmrc/checkpoint-1493 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v43/webqa1_cmrc1_drcd --model_type bert --train_file train_drcd.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v43/webqa1_cmrc1_drcd
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v43/webqa1_cmrc1_drcd/checkpoint-2569 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v43/webqa1_cmrc1_drcd1_cail --model_type bert --train_file train_cail.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 2 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v43/webqa1_cmrc1_drcd1_cail
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v43/webqa1_cmrc1_drcd1_cail/checkpoint-3874 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v43/webqa1_cmrc1_drcd1_cail1_lic --model_type bert --train_file train_lic.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v43/webqa1_cmrc1_drcd1_cail1_lic
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v43/webqa1_cmrc1_drcd/checkpoint-2569 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v43/webqa1_cmrc1_drcd --model_type bert --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 12 --model_name chinese-roberta-wwm-ext-large --output_result_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v43/webqa1_cmrc1_drcd
```

drwxr-xr-x 1 mqq mqq 1302306293 May 16 19:36 checkpoint-10869
drwxr-xr-x 1 mqq mqq 1302306293 May 16 14:56 checkpoint-5435

drwxr-xr-x 1 mqq mqq 1302306319 May 16 21:20 checkpoint-1493
drwxr-xr-x 1 mqq mqq 1302306319 May 16 22:37 checkpoint-2985

drwxr-xr-x 1 mqq mqq 1302306317 May 17 01:06 checkpoint-2569
drwxr-xr-x 1 mqq mqq 1302306317 May 17 03:18 checkpoint-5137

drwxr-xr-x 1 mqq mqq 1302306334 May 17 14:02 checkpoint-1643
drwxr-xr-x 1 mqq mqq 1302306334 May 17 14:44 checkpoint-2464
drwxr-xr-x 1 mqq mqq 1302306334 May 17 15:26 checkpoint-3285
drwxr-xr-x 1 mqq mqq 1302306334 May 17 16:09 checkpoint-4106
drwxr-xr-x 1 mqq mqq 1302306334 May 17 13:19 checkpoint-822

```shell
python test_multi_2.py 
--data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_type bert --predict_file test2_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --max_answer_length 40 --per_gpu_eval_batch_size 8 --n_best_size 20 --split_doc --do_lower_case --threads 12 --model_name chinese-roberta-wwm-ext-large --output_all_logit --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v43/webqa1_cmrc1_drcd1_cail1_lic/checkpoint-4106 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v43/webqa1_cmrc1_drcd1_cail1_lic/checkpoint-3285 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v43/webqa1_cmrc1_drcd1_cail1_lic/checkpoint-2464 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v43/webqa1_cmrc1_drcd1_cail1_lic/checkpoint-1643 --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v43/webqa1_cmrc1_drcd1_cail1_lic/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_data_join_v43/webqa1_cmrc1_drcd1_cail1_lic
```



## RoBERTa-large

### V1

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/chinese-roberta-wwm-ext-large --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v1 --model_type bert --train_file train.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 3 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v1/checkpoint-6571 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v1/ --model_type bert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --threads 3 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 3898214992 4月  10 19:54 checkpoint-3286
drwxr-xr-x 1 mqq mqq 3898214992 4月  10 20:43 checkpoint-6571
drwxr-xr-x 1 mqq mqq 3898214992 4月  10 21:32 checkpoint-9856

### V2

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/chinese-roberta-wwm-ext-large --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v2 --model_type bert --train_file train.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v2/checkpoint-2464 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v2/ --model_type bert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 3898214958 4月  10 20:33 checkpoint-1643
drwxr-xr-x 1 mqq mqq 3898214958 4月  10 21:15 checkpoint-2464
drwxr-xr-x 1 mqq mqq 3898214602 4月  11 13:41 checkpoint-3285
drwxr-xr-x 1 mqq mqq 3898214602 4月  11 14:24 checkpoint-4106
drwxr-xr-x 1 mqq mqq 3898214958 4月  10 19:51 checkpoint-822

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v2/checkpoint-4106 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v2/ --model_type bert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --output_all_logit --overwrite_cache
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join --model_name_or_path  /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v2/checkpoint-4106 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v2/ --model_type bert --predict_file train_extended_v4.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```



### V3

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/chinese-roberta-wwm-ext-large --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v3 --model_type bert --train_file train.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 8 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v3/checkpoint-1641 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v3/ --model_type bert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 8 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 3898214966 4月  11 01:54 checkpoint-1231
drwxr-xr-x 1 mqq mqq 3898214966 4月  11 02:35 checkpoint-1641
drwxr-xr-x 1 mqq mqq 3898214966 4月  11 03:17 checkpoint-2051
drwxr-xr-x 1 mqq mqq 3898214966 4月  11 00:32 checkpoint-411
drwxr-xr-x 1 mqq mqq 3898214966 4月  11 01:13 checkpoint-821



### V4

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/chinese-roberta-wwm-ext-large --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v4 --model_type bert --train_file train.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 16 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v4/checkpoint-411 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v4/ --model_type bert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 16 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 3898214964 4月  11 03:15 checkpoint-1026
drwxr-xr-x 1 mqq mqq 3898214572 4月  11 00:33 checkpoint-206
drwxr-xr-x 1 mqq mqq 3898214964 4月  11 01:13 checkpoint-411
drwxr-xr-x 1 mqq mqq 3898214964 4月  11 01:54 checkpoint-616
drwxr-xr-x 1 mqq mqq 3898214964 4月  11 02:35 checkpoint-821



### V5

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/chinese-roberta-wwm-ext-large --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v5 --model_type bert --train_file train.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 384 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 4 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --overwrite_cache --gradient_accumulation_steps 8
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v5/checkpoint-2569 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v5/ --model_type bert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 384 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --overwrite_cache --gradient_accumulation_steps 8
```


drwxr-xr-x 1 mqq mqq 3898214982 4月  11 01:52 checkpoint-1285
drwxr-xr-x 1 mqq mqq 3898214982 4月  11 02:46 checkpoint-1927
drwxr-xr-x 1 mqq mqq 3898214982 4月  11 03:41 checkpoint-2569
drwxr-xr-x 1 mqq mqq 3898214982 4月  11 04:35 checkpoint-3211
drwxr-xr-x 1 mqq mqq 3898214982 4月  11 00:57 checkpoint-643



### V6

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/chinese-roberta-wwm-ext-large --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v6 --model_type bert --train_file train.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 512 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 4 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 8 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v6/checkpoint-2761 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v6/ --model_type bert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 512 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 8 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 3898214958 4月  11 02:43 checkpoint-1105
drwxr-xr-x 1 mqq mqq 3898214958 4月  11 03:46 checkpoint-1657
drwxr-xr-x 1 mqq mqq 3898214958 4月  11 04:48 checkpoint-2209
drwxr-xr-x 1 mqq mqq 3898214958 4月  11 05:51 checkpoint-2761
drwxr-xr-x 1 mqq mqq 3898214958 4月  11 01:41 checkpoint-553



### V7

ChineseMRC_V1:在bert后面，预测层前面 加绝对位置

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/chinese-roberta-wwm-ext-large --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v7 --model_type bert --train_file train.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v7/checkpoint-3285 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v7/ --model_type bert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 1306406378 Apr 22 01:10 checkpoint-1643
drwxr-xr-x 1 mqq mqq 1306406378 Apr 22 01:52 checkpoint-2464
drwxr-xr-x 1 mqq mqq 1306406378 Apr 22 02:34 checkpoint-3285
drwxr-xr-x 1 mqq mqq 1306406378 Apr 22 03:17 checkpoint-4106
drwxr-xr-x 1 mqq mqq 1306406378 Apr 22 00:27 checkpoint-822



### V8

ChineseMRC_V2:加入absolute position embedding

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/chinese-roberta-wwm-ext-large --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v8 --model_type bert --train_file train.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --use_absolute_position
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v8/checkpoint-4106 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v8 --model_type bert --train_file train.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --use_absolute_position --inherit_global_step
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v8/checkpoint-4106 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v8/ --model_type bert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --use_absolute_position
```

drwxr-xr-x 1 mqq mqq 1306406472 4月  25 16:05 checkpoint-1643
drwxr-xr-x 1 mqq mqq 1306406472 4月  25 16:47 checkpoint-2464
drwxr-xr-x 1 mqq mqq 1306406472 4月  25 17:30 checkpoint-3285
drwxr-xr-x 1 mqq mqq 1306406472 4月  25 18:12 checkpoint-4106
drwxr-xr-x 1 mqq mqq 1306406584 4月  25 22:19 checkpoint-4927
drwxr-xr-x 1 mqq mqq 1306406584 4月  25 23:02 checkpoint-5748
drwxr-xr-x 1 mqq mqq 1306406584 4月  25 23:44 checkpoint-6569
drwxr-xr-x 1 mqq mqq 1306406472 4月  25 15:23 checkpoint-822

### V9

ChineseMRC_V3:

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/keywords_data --model_name_or_path /ceph/qbkg/aitingliu/MRC/chinese-roberta-wwm-ext-large --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v9 --model_type bert --train_file train_kw_tfidf.json --predict_file dev_kw_tfidf.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/keywords_data --model_name_or_path  /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v9/checkpoint-2464 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v9/ --model_type bert --predict_file test1_dealed_kw_tfidf.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 1302314540 Apr 29 02:12 checkpoint-1643
drwxr-xr-x 1 mqq mqq 1302314540 Apr 29 02:54 checkpoint-2464
drwxr-xr-x 1 mqq mqq 1302314540 Apr 29 03:37 checkpoint-3285
drwxr-xr-x 1 mqq mqq 1302314540 Apr 29 04:19 checkpoint-4106
drwxr-xr-x 1 mqq mqq 1302314530 Apr 29 01:29 checkpoint-822

-rw-r--r-- 1 mqq mqq   2468944 Apr 29 00:01 dev_kw_tfidf.json
-rw-r--r-- 1 mqq mqq  68892207 Apr 29 00:01 test1_dealed_kw_tfidf.json
-rw-r--r-- 1 mqq mqq  24259901 Apr 29 00:01 train_kw_tfidf.json



### V10

ChineseMRC_V3:use_context_keyword

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/keywords_data --model_name_or_path /ceph/qbkg/aitingliu/MRC/chinese-roberta-wwm-ext-large --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v10 --model_type bert --train_file train_kw_tfidf.json --predict_file dev_kw_tfidf.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --use_context_keyword
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/keywords_data --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v10/checkpoint-2464 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v10/ --model_type bert --predict_file test1_dealed_kw_tfidf.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large --use_context_keyword
```

drwxr-xr-x 1 mqq mqq 1302314525 Apr 29 12:13 checkpoint-1643
drwxr-xr-x 1 mqq mqq 1302314525 Apr 29 12:56 checkpoint-2464
drwxr-xr-x 1 mqq mqq 1302314525 Apr 29 13:38 checkpoint-3285
drwxr-xr-x 1 mqq mqq 1302314525 Apr 29 14:21 checkpoint-4106
drwxr-xr-x 1 mqq mqq 1302314525 Apr 29 11:31 checkpoint-822

### V11

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v11/pretrain/checkpoint-3774 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v11 --model_type bert --train_file train.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v11/checkpoint-4106 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v11/ --model_type bert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 1302306193 May  5 01:04 checkpoint-1643
drwxr-xr-x 1 mqq mqq 1302306193 May  5 01:46 checkpoint-2464
drwxr-xr-x 1 mqq mqq 1302306193 May  5 02:28 checkpoint-3285
drwxr-xr-x 1 mqq mqq 1302306193 May  5 03:11 checkpoint-4106
drwxr-xr-x 1 mqq mqq 1302306193 May  5 00:21 checkpoint-822

### V12

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join/ --model_name_or_path /ceph/qbkg/aitingliu/MRC/chinese-roberta-wwm-ext-large --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v12 --model_type bert --train_file train_lic_part1.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020/data_join/ --model_name_or_path /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v12/checkpoint-2876 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_large_v12/ --model_type bert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 4 --threads 3 --model_name chinese-roberta-wwm-ext-large
```

drwxr-xr-x 1 mqq mqq 1302306051 May  9 18:59 checkpoint-1151
drwxr-xr-x 1 mqq mqq 1302306051 May  9 19:29 checkpoint-1726
drwxr-xr-x 1 mqq mqq 1302306051 May  9 19:58 checkpoint-2301
drwxr-xr-x 1 mqq mqq 1302306051 May  9 20:28 checkpoint-2876
drwxr-xr-x 1 mqq mqq 1302306051 May  9 18:30 checkpoint-576



## ALBERT-xlarge

### V1

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/albert_chinese_xlarge --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_xlarge_v1 --model_type albert --train_file train.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 16 --do_train --learning_rate 2e-5 --num_train_epochs 3 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --overwrite_cache
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_xlarge_v1/checkpoint-1644 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_xlarge_v1/ --model_type albert --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --overwrite_cache
```


drwxr-xr-x 1 mqq mqq 657675573 4月  10 21:04 checkpoint-1644
drwxr-xr-x 1 mqq mqq 657675573 4月  10 22:42 checkpoint-3287
drwxr-xr-x 1 mqq mqq 657675573 4月  11 00:19 checkpoint-4930

### V2

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/albert_chinese_xlarge --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_xlarge_v2 --model_type albert --train_file train.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 16 --do_train --learning_rate 2e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.05 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --overwrite_cache --gradient_accumulation_steps 2
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_xlarge_v2/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_xlarge_v2/ --model_type albert --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.05 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --overwrite_cache --gradient_accumulation_steps 2
```

drwxr-xr-x 1 mqq mqq 657675573 4月  11 18:33 checkpoint-1643
drwxr-xr-x 1 mqq mqq 657675573 4月  11 20:11 checkpoint-2464
drwxr-xr-x 1 mqq mqq 657675573 4月  11 21:49 checkpoint-3285
drwxr-xr-x 1 mqq mqq 657675573 4月  11 23:27 checkpoint-4106
drwxr-xr-x 1 mqq mqq 657675573 4月  11 16:54 checkpoint-822

### V3

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/albert_chinese_xlarge --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_xlarge_v3 --model_type albert --train_file train.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 384 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 2e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.05 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --overwrite_cache --gradient_accumulation_steps 4
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_xlarge_v3/checkpoint-1643 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_xlarge_v3/ --model_type albert --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 384 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.05 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --overwrite_cache --gradient_accumulation_steps 4
```



### V4

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/albert_chinese_xlarge --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_xlarge_v4 --model_type albert --train_file train.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 512 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 2e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.05 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --overwrite_cache --gradient_accumulation_steps 4
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_xlarge_v4/checkpoint-553 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_xlarge_v4/ --model_type albert --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 512 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.05 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --overwrite_cache --gradient_accumulation_steps 4
```



drwxr-xr-x 1 mqq mqq 657675571 4月  11 19:57 checkpoint-1105
drwxr-xr-x 1 mqq mqq 657675571 4月  11 22:14 checkpoint-1657
drwxr-xr-x 1 mqq mqq 657675571 4月  12 00:31 checkpoint-2209
drwxr-xr-x 1 mqq mqq 657675571 4月  12 02:48 checkpoint-2761
drwxr-xr-x 1 mqq mqq 657675571 4月  11 17:40 checkpoint-553



## ALBERT-xxlarge

### V1

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/albert_chinese_xxlarge --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_xxlarge_v1 --model_type albert --train_file train.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 4 --do_train --learning_rate 2e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --overwrite_cache
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_xxlarge_v1/checkpoint-19708 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_xxlarge_v1/ --model_type albert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --overwrite_cache --threads 3
```

drwxr-xr-x 1 mqq mqq 2523493679 4月  11 02:30 checkpoint-13139
drwxr-xr-x 1 mqq mqq 2523493679 4月  11 05:51 checkpoint-19708
drwxr-xr-x 1 mqq mqq 2523493514 4月  11 23:09 checkpoint-26276
drwxr-xr-x 1 mqq mqq 2523493514 4月  12 02:30 checkpoint-32845
drwxr-xr-x 1 mqq mqq 2523493679 4月  10 23:08 checkpoint-6570



### V2

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/albert_chinese_xxlarge --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_xxlarge_v2 --model_type albert --train_file train.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 4 --do_train --learning_rate 2e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 8 --threads 3 --model_name albert_chinese_xxlarge
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_xxlarge_v2/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_xxlarge_v2/ --model_type albert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 8 --threads 3 --model_name albert_chinese_xxlarge
```

drwxr-xr-x 1 mqq mqq 2523493679 4月  11 02:17 checkpoint-1643
drwxr-xr-x 1 mqq mqq 2523493679 4月  11 05:32 checkpoint-2464
drwxr-xr-x 1 mqq mqq 2523493591 4月  11 23:00 checkpoint-3285
drwxr-xr-x 1 mqq mqq 2523493591 4月  12 02:14 checkpoint-4106
drwxr-xr-x 1 mqq mqq 2523493679 4月  10 23:03 checkpoint-822

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_xxlarge_v2/checkpoint-822 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_xxlarge_v2/ --model_type albert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 8 --threads 3 --model_name albert_chinese_xxlarge --output_all_logit --overwrite_cache
```



### V3

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/albert_chinese_xxlarge --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_xxlarge_v3 --model_type albert --train_file train.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 384 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 2 --do_train --learning_rate 2e-5 --num_train_epochs 3 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 16 --threads 3 --model_name albert_chinese_xxlarge
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_xxlarge_v3/checkpoint-1924 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_xxlarge_v3/ --model_type albert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 384 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 16 --threads 3 --model_name albert_chinese_xxlarge
```

drwxr-xr-x 1 mqq mqq 2523493683 4月  12 00:21 checkpoint-1283
drwxr-xr-x 1 mqq mqq 2523493683 4月  12 04:17 checkpoint-1924
drwxr-xr-x 1 mqq mqq 2523493683 4月  11 20:27 checkpoint-642



### V4

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/albert_chinese_xxlarge --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_xxlarge_v4 --model_type albert --train_file train.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 512 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 1 --do_train --learning_rate 2e-5 --num_train_epochs 3 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 32 --threads 3 --model_name albert_chinese_xxlarge
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_xxlarge_v4/checkpoint-1657 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_xxlarge_v4/ --model_type albert --predict_file test1_dealed.json --do_eval --overwrite_output_dir --max_seq_length 512 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --gradient_accumulation_steps 32 --threads 3 --model_name albert_chinese_xxlarge
```

drwxr-xr-x 1 mqq mqq 2523493663 4月  12 02:26 checkpoint-1105
drwxr-xr-x 1 mqq mqq 2523493663 4月  12 07:15 checkpoint-1657
drwxr-xr-x 1 mqq mqq 2523493663 4月  11 21:38 checkpoint-553



## BERT-wwm-ext

### V1

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/chinese-bert-wwm-ext --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_bert_wwm_ext_v1 --model_type bert --train_file train.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 32 --do_train --learning_rate 3e-5 --num_train_epochs 3 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --overwrite_cache
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/output/lic2020_bert_wwm_ext_v1/checkpoint-823 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_bert_wwm_ext_v1/ --model_type bert --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --overwrite_cache
```


drwxr-xr-x 1 mqq mqq 1222721705 4月  10 20:21 checkpoint-1645
drwxr-xr-x 1 mqq mqq 1222721705 4月  10 20:34 checkpoint-2467
drwxr-xr-x 1 mqq mqq 1222721705 4月  10 20:08 checkpoint-823



### V2

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/chinese-bert-wwm-ext --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_bert_wwm_ext_v2 --model_type bert --train_file train.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 384 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 3 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --overwrite_cache --gradient_accumulation_steps 4
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/output/lic2020_bert_wwm_ext_v2/checkpoint-643 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_bert_wwm_ext_v2/ --model_type bert --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 384 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --overwrite_cache --gradient_accumulation_steps 4
```

drwxr-xr-x 1 mqq mqq 1222721691 4月  11 18:17 checkpoint-1285
drwxr-xr-x 1 mqq mqq 1222721691 4月  11 18:41 checkpoint-1927
drwxr-xr-x 1 mqq mqq 1222721691 4月  11 17:53 checkpoint-643



### V3

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/chinese-bert-wwm-ext --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_bert_wwm_ext_v3 --model_type bert --train_file train.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 512 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 3 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --overwrite_cache --gradient_accumulation_steps 4
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/output/lic2020_bert_wwm_ext_v3/checkpoint-553 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_bert_wwm_ext_v3/ --model_type bert --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 512 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --overwrite_cache --gradient_accumulation_steps 4
```

drwxr-xr-x 1 mqq mqq 1222721643 4月  11 17:40 checkpoint-1105
drwxr-xr-x 1 mqq mqq 1222721643 4月  11 18:00 checkpoint-1657
drwxr-xr-x 1 mqq mqq 1222721643 4月  11 17:19 checkpoint-553







# 测试ChineseMRC代码

## ALBERT

### V1

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/albert_chinese_base --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_models_v1 --model_type albert --train_file train.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 32 --do_train --learning_rate 2e-5 --num_train_epochs 3 --n_best_size 10 --split_doc --overwrite_cache
```


```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_models_v1/checkpoint-2452 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_models_v1/ --model_type albert --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --overwrite_cache
```

drwxr-xr-x 1 mqq mqq 121995511 4月   5 14:40 checkpoint-1635
drwxr-xr-x 1 mqq mqq 121995511 4月   5 14:55 checkpoint-2452
drwxr-xr-x 1 mqq mqq 121995511 4月   5 17:08 checkpoint-3269
drwxr-xr-x 1 mqq mqq 121995511 4月   5 17:18 checkpoint-4086
drwxr-xr-x 1 mqq mqq 121995511 4月   5 14:24 checkpoint-818



### V2

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/albert_chinese_large --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_models_v2 --model_type albert --train_file train.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 5e-5 --num_train_epochs 3 --n_best_size 10 --overwrite_cache
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_models_v2/checkpoint-5446 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_models_v2/ --model_type albert --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --overwrite_cache
```


drwxr-xr-x 1 mqq mqq 190334214 4月   6 21:22 checkpoint-1816
drwxr-xr-x 1 mqq mqq 190334214 4月   6 21:41 checkpoint-3631
drwxr-xr-x 1 mqq mqq 190334214 4月   6 22:00 checkpoint-5446



### V3

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/albert_chinese_xlarge --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_models_v3 --model_type albert --train_file train.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 16 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --overwrite_cache
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_models_v3/checkpoint-2452 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_models_v3/ --model_type albert --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --overwrite_cache
```


drwxr-xr-x 1 mqq mqq 691246880 4月   5 19:04 checkpoint-1635
drwxr-xr-x 1 mqq mqq 691246880 4月   5 19:53 checkpoint-2452
drwxr-xr-x 1 mqq mqq 691246880 4月   5 20:43 checkpoint-3269
drwxr-xr-x 1 mqq mqq 691246880 4月   5 21:32 checkpoint-4086
drwxr-xr-x 1 mqq mqq 691246880 4月   5 18:15 checkpoint-818



### V4

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/albert_chinese_xlarge --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_models_v4 --model_type albert --train_file train.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 512 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --overwrite_cache
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_models_v4/checkpoint-6613 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_models_v4/ --model_type albert --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 512 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --overwrite_cache
```


drwxr-xr-x 1 mqq mqq 657675511 4月   6 04:50 checkpoint-11021
drwxr-xr-x 1 mqq mqq 657675511 4月   5 19:43 checkpoint-2205
drwxr-xr-x 1 mqq mqq 657675511 4月   5 22:00 checkpoint-4409
drwxr-xr-x 1 mqq mqq 657675511 4月   6 00:16 checkpoint-6613
drwxr-xr-x 1 mqq mqq 657675511 4月   6 02:34 checkpoint-8817



### V5

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/albert_chinese_xxlarge --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_models_v5 --model_type albert --train_file train.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 4 --do_train --learning_rate 2e-5 --num_train_epochs 3 --n_best_size 10 --split_doc --warmup_proportion 0.1 --overwrite_cache
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_models_v5/checkpoint-19606 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_models_v5/ --model_type albert --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --overwrite_cache
```


drwxr-xr-x 1 mqq mqq 2523493686 4月   8 03:45 checkpoint-13071
drwxr-xr-x 1 mqq mqq 2523493686 4月   8 07:02 checkpoint-19606
drwxr-xr-x 1 mqq mqq 2523493686 4月   8 00:28 checkpoint-6536



### V6

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/albert_chinese_large --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_models_v6 --model_type albert --train_file train.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 32 --do_train --learning_rate 2e-5 --num_train_epochs 3 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --overwrite_cache
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_models_v6/checkpoint-2452 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_albert_models_v6/ --model_type albert --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --overwrite_cache
```


drwxr-xr-x 1 mqq mqq 190334248 4月   7 23:47 checkpoint-1635
drwxr-xr-x 1 mqq mqq 190334248 4月   8 00:18 checkpoint-2452
drwxr-xr-x 1 mqq mqq 190334248 4月   7 23:16 checkpoint-818





## BERT

### V1

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/bert-base-chinese --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_bert_models_v1 --model_type bert --train_file train.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 32 --do_train --learning_rate 3e-5 --num_train_epochs 5 --n_best_size 10 --split_doc --overwrite_cache
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/output/lic2020_bert_models_v1/checkpoint-1363 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_bert_models_v1/ --model_type bert --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --overwrite_cache
```


drwxr-xr-x 1 mqq mqq 1222721780 4月   6 18:43 checkpoint-1363
drwxr-xr-x 1 mqq mqq 1222721780 4月   6 18:51 checkpoint-1817
drwxr-xr-x 1 mqq mqq 1222721780 4月   6 18:58 checkpoint-2271
drwxr-xr-x 1 mqq mqq 1222721780 4月   6 18:28 checkpoint-455
drwxr-xr-x 1 mqq mqq 1222721780 4月   6 18:36 checkpoint-909





### V2

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/chinese-bert-wwm-ext --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_bert_models_v2 --model_type bert --train_file train.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 32 --do_train --learning_rate 3e-5 --num_train_epochs 3 --n_best_size 10 --split_doc --warmup_proportion 0.1 --overwrite_cache
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/output/lic2020_bert_models_v2/checkpoint-2452 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_bert_models_v2/ --model_type bert --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --overwrite_cache
```


drwxr-xr-x 1 mqq mqq 1222721700 4月   7 19:05 checkpoint-1635
drwxr-xr-x 1 mqq mqq 1222721700 4月   7 19:24 checkpoint-2452
drwxr-xr-x 1 mqq mqq 1222721700 4月   7 18:46 checkpoint-818





## RoBERTa

### V1

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/chinese-roberta-wwm-ext-large --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_models_v1 --model_type bert --train_file train.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 3 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --overwrite_cache
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_models_v1/checkpoint-3269 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_models_v1/ --model_type bert --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --overwrite_cache
```

drwxr-xr-x 1 mqq mqq 3898214214 4月   8 19:54 checkpoint-3269
drwxr-xr-x 1 mqq mqq 3898214214 4月   8 20:42 checkpoint-6537
drwxr-xr-x 1 mqq mqq 3898214214 4月   8 21:31 checkpoint-9805

### V2

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/chinese-roberta-wwm-ext-large --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_models_v2 --model_type bert --train_file train.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 3 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --overwrite_cache
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_models_v2/checkpoint-6537 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_models_v2/ --model_type bert --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --overwrite_cache
```


drwxr-xr-x 1 mqq mqq 3898214994 4月   8 23:56 checkpoint-3269
drwxr-xr-x 1 mqq mqq 3898214994 4月   9 00:45 checkpoint-6537
drwxr-xr-x 1 mqq mqq 3898214994 4月   9 01:35 checkpoint-9805



### V3

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/chinese-roberta-wwm-ext-large --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_models_v3 --model_type bert --train_file train.json --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --per_gpu_train_batch_size 8 --do_train --learning_rate 3e-5 --num_train_epochs 3 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --overwrite_cache
```

```shell
python run.py --data_dir /ceph/qbkg/aitingliu/MRC/data/lic2020 --model_name_or_path  /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_models_v3/checkpoint-6537 --output_dir /ceph/qbkg/aitingliu/MRC/output/lic2020_roberta_models_v3/ --model_type bert --predict_file dev.json --do_eval --overwrite_output_dir --max_seq_length 256 --per_gpu_eval_batch_size 8 --n_best_size 10 --split_doc --warmup_proportion 0.1 --seed 12345 --weight_decay 0.01 --adam_epsilon 1e-6 --do_lower_case --overwrite_cache
```


drwxr-xr-x 1 mqq mqq 3898214983 4月   8 23:57 checkpoint-3269
drwxr-xr-x 1 mqq mqq 3898214983 4月   9 00:47 checkpoint-6537
drwxr-xr-x 1 mqq mqq 3898214983 4月   9 01:36 checkpoint-9805



