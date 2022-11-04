## change_tips
R script for tree tips edition

## Usage 
```r
library(seqinr)
library(ape)

seq <- read.fasta("input.aligned.fasta")
tree <- read.tree("raw_tree.nwk")

change_tips(tree = tree, sequences = seq, output_name = "new_tree.nwk")
```

## The code
```r
library(seqinr)
library(ape)
change_tips <- function(tree,sequences,output_name){
seq <- sequences
tree <- tree
output_name <- output_name
seq2 <- data.frame(order_seq=1:length(names(seq)),seq_names=names(seq))
seq3 <- seq2[order(seq2$seq_names),]
names(tree)
tree$tip.label
l <- data.frame(order_tree=1:length(tree$tip.label),original_tree=tree$tip.label)
l2 <- l[order(l$original_tree),]
d <- data.frame(l2,seq3)
e <- d[order(d$order_tree),]
tree$tip.label <- e$seq_names
write.tree(tree, output_name)
}
```
