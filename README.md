# ioi-circuit-listing
Everything we know about the IOI Circuit in Mamba

Sorted by fact and evidence for that fact

I recommend browsing using table of contents (on the right hand of your screen)

# Layer 0 and 39 important
## Resample Ablation

Patch `hook_layer_input`

![Patch hook_layer_input](https://raw.githubusercontent.com/Phylliida/ioi-circuit-listing/main/figures/combined%20patchings.png) 

Patch `hook_h`

![Patch h](https://raw.githubusercontent.com/Phylliida/ioi-circuit-listing/main/figures/hook%20h.png) 

## Layer Removal

Layer removal (zero ablate layer outputs), show relative answer pr

![Layer removal prs](https://raw.githubusercontent.com/Phylliida/ioi-circuit-listing/main/figures/remove%20layer%20relative%20prs.png)

# Other Layers

## Layer 0 doesn't usually need cross talk

Proportion in minimal cross talk circuit doesn't usually have 0

![Layer removal prs](https://raw.githubusercontent.com/Phylliida/ioi-circuit-listing/main/figures/proportaion%20in%20minimal%20circuit%20cropped.png)

Not too suprising because all names/entities are single token

## Sufficient information to predict the any name at all later, after layer 0

![Linear probe](https://raw.githubusercontent.com/Phylliida/ioi-circuit-listing/main/figures/linear%20probe.png) 

Did same thing for other positions and got same results

## Layer 15 is likely to do cross talk

Always occured (usually the second one added)

![Layer removal prs](https://raw.githubusercontent.com/Phylliida/ioi-circuit-listing/main/figures/proportaion%20in%20minimal%20circuit%20cropped.png)

## Cross talk is needed before 39 for last two tokens

See [Replace names](#replace-names)
Layer 39 Representations are Linear, 1-3 compatible with each other, 4-5 not compatible with 1-3.

Conv has no way of distinguishing 5 from 3 (can't attend back far enough), so some earlier layer does this. Alternatively could be artifact of method

# Layer 39

## Convs shift one token forward

### Cosine sim (not causal)

![cosine sim](https://raw.githubusercontent.com/Phylliida/ioi-circuit-listing/main/figures/cosine%20sim%20merged.png)

### Resample ablation on conv slices (causal)

![conv patch merged](https://raw.githubusercontent.com/Phylliida/ioi-circuit-listing/main/figures/conv%20patch%20merged.png)

## SSM takes in tokens at that shifted location

We can modify the activations at `ssm_input` to change the output to any desired name, suggesting those positions are what matters

### Replace names

Proportion of data where logit of the corrupted name is higher than the logit of original name, using the two methods described in Section ~\ref{overwritename}. The x-axis is the position the average was computed from, the y-axis is the position being substituted. To substitute into the fourth and fifth positions, we substitute the correct answer (instead of a patched name).

![replace names](https://raw.githubusercontent.com/Phylliida/ioi-circuit-listing/main/figures/replace%20names%20plot%20merged.png)

## Moves tokens info to last token

### Resample Ablation

Patch on `blocks.{layer}.hook_h.{token_pos}`

![patch on hook_h](https://raw.githubusercontent.com/Phylliida/ioi-circuit-listing/main/figures/hook%20h.png)

### Cosine sim

![cosine sim](https://raw.githubusercontent.com/Phylliida/ioi-circuit-listing/main/figures/cosine%20sim%20merged.png)


# Circuit Discovery

## Adjacency matrices

On all (5) patchings, EAP on left, ACDC on right

![comparison acdc eap](https://raw.githubusercontent.com/Phylliida/ioi-circuit-listing/main/figures/comparison%20acdc%20eap.png)

## EAP full results

For these we just show whether or not the edge was present, to get acc 85%.

### Over all token positions

![comparison acdc eap](https://raw.githubusercontent.com/Phylliida/ioi-circuit-listing/main/figures/no%20positions%20eap.png)

### Per token

<details>
  <summary></summary>
  
  Spoiler text. Note that it's important to have a space after the summary tag. You should be able to write any markdown you want inside the `<details>` tag... just make sure you close `<details>` afterward.
  
  ```javascript
  console.log("I'm a code block!");
  ```
  
</details>

