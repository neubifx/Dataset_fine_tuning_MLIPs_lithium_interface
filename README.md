# Dataset_fine_tuning_MLIPs_lithium_interface

Repository containing the DFT dataset and code used for fine-tuned MACE models for Li metal interfaces.

## Training scripts

### Fine-tuning from MACE-MP-0

```
  --name="MACE_test" \
  --foundation_model="medium" \
  --train_file="01_train/full_train_dataset.xyz" \
  --valid_fraction=0.1 \
  --test_file="02_test/full_test_dataset.xyz" \
  --energy_key="ref_energy" \
  --forces_key="ref_forces" \
  --energy_weight=1.0 \
  --forces_weight=10.0 \
  --E0s="average" \
  --lr=0.05 \
  --scaling="rms_forces_scaling" \
  --batch_size=2 \
  --max_num_epochs=100 \
  --ema \
  --ema_decay=0.99 \
  --amsgrad \
  --default_dtype="float32" \
  --device=cuda \
  --seed=3

```

### Multihead fine-tuning from MACE-MP-0

```
  --name="MACE_test" \
  --foundation_model="${MACE_ROOT}/.cache/mace/5yyxdm76" \
  --multiheads_finetuning=True \
  --train_file="01_train/full_train_dataset.xyz" \
  --valid_fraction=0.1 \
  --test_file="02_test/full_test_dataset.xyz" \
  --energy_key="REF_energy" \
  --forces_key="REF_forces" \
  --energy_weight=1.0 \
  --forces_weight=10.0 \
  --E0s="foundation" \
  --lr=0.05 \
  --scaling="rms_forces_scaling" \
  --batch_size=2 \
  --max_num_epochs=100 \
  --ema \
  --ema_decay=0.99 \
  --amsgrad \
  --pt_train_file="mp" \
  --default_dtype="float64" \
  --device=cuda \
  --seed=3

```

