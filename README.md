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


On Gadi you generally don’t pick a specific node; you describe the resources you need and PBS picks a matching node. So the trick is:

Figure out what your job actually needs

CPU-only vs GPU

How many cores (ncpus)?

How much RAM (mem)?

Do you need big RAM (→ hugemem) or GPUs (→ gpu… queue)?

Heavy scratch I/O (→ add jobfs)


```
# General CPU job (normal queue)
qsub -I -q normal -l walltime=1:00:00,ncpus=8,mem=32GB,jobfs=20GB,wd,storage=gdata/<proj>+scratch/<proj>

# High-memory CPU job
qsub -I -q hugemem -l walltime=1:00:00,ncpus=8,mem=512GB,wd,storage=gdata/<proj>+scratch/<proj>

# GPU job (V100 queue name on Gadi is often gpuvolta)
qsub -I -q gpuvolta -l walltime=1:00:00,ncpus=8,mem=32GB,ngpus=1,jobfs=50GB,wd,storage=gdata/<proj>+scratch/<proj>

```
