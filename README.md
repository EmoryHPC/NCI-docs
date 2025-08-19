# NCI-docs

on NCI Gadi, the scheduler is PBS Pro not Slurm. 

see all nodes: 

```
qstat -Q
```

See node details

```
pbsnodes -a
```

```
module purge
module load ENTER
```


3. Check your jobs and assigned nodes

qstat -u $USER
