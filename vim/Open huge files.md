# Open huge files quickly with vim (tested on a 1.5Go file)
open vim only
type :set binary
type :open filename

# Other solution : don't open huge files with vim, split them with the following command :
split -b 100M filename

It will create files named xaa, xab...
Vim will open them and you can concatenate them after editing.
